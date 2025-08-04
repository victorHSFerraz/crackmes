int main(int argc,char **argv)

{
  int random_number;
  size_t input_length;
  char *user_input;
  undefined8 extraout_RDX;
  undefined8 extraout_RDX_00;
  undefined8 extraout_RDX_01;
  undefined8 extraout_RDX_02;
  undefined8 uVar1;
  ulong uVar2;
  char *message;
  undefined8 in_R8;
  undefined8 in_R9;
  long in_FS_OFFSET;
  ulong i;
  char encoded_password [9];
  ulong stack;
  bool password_match;
  
  stack = *(ulong *)(in_FS_OFFSET + 0x28);
  if (argc == 2) {
    input_length = strlen(argv[1]);
                    /* check if the input length have 9 characters */
    if (input_length == 9) {
                    /* decodes the reference string using Caesar cipher, doing shifts for each
                       character using a fixed random seed  */
      builtin_strncpy(encoded_password,"gssw#tpcz",9);
      password_match = false;
      srandom(0x7bf);
      for (i = 0; i < 9; i = i + 1) {
        random_number = rand();
        encoded_password[i] = encoded_password[i] - ((char)(random_number % 5) + '\x01');
                    /* compares each character, the answer is "dont play" */
        user_input = argv[1];
        if (encoded_password[i] != user_input[i]) {
          password_match = true;
          break;
        }
      }
      if (password_match) {
        message = "Wrong Password !!!";
        puts("Wrong Password !!!");
        uVar1 = extraout_RDX_01;
      }
      else {
        message = "Congratulation !!!";
        puts("Congratulation !!!");
        uVar1 = extraout_RDX_02;
      }
    }
    else {
      message = "Wrong Password !!!";
      puts("Wrong Password !!!");
      uVar1 = extraout_RDX_00;
    }
  }
  else {
    message = "Use ./WarGames pass";
    puts("Use ./WarGames pass");
    uVar1 = extraout_RDX;
  }
  uVar2 = stack ^ *(ulong *)(in_FS_OFFSET + 0x28);
  if (uVar2 == 0) {
    return 0;
  }
                    /* WARNING: Subroutine does not return */
  __stack_chk_fail(message,uVar2,uVar1,user_input,in_R8,in_R9);
