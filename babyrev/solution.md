
int main(void)

{
  int isValidPassword;
  long in_FS_OFFSET;
  int codePin;
  uint local_3c;
  char password [40];
  long local_10;
  
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  puts("Welcome to baby rev challenge\nInput the password:\n");
  fgets(password,0x20,stdin);
  puts("Input the secret code now:\n");
  __isoc99_scanf(&DAT_0010211f,&codePin);
  if (codePin == 0x539) {                                                    //check if code = 1337
    isValidPassword = strcmp(password,"Sup3rS3cr3tP455W0rd\n");              //check if passwd = Sup3rS3cr3tP455W0rd
    if (isValidPassword == 0) {                                              
      puts("Correct!\nHere is your flag\n");                                //CTFlearn{W4s_1T_Th4T_H4rd?} 
      for (local_3c = 0; local_3c < 0x1b; local_3c = local_3c + 1) {
        putchar((int)(char)((char)local_3c + 0x69U ^
                           (byte)*(undefined4 *)(flag + (long)(int)local_3c * 4)));
      }
    }
    else {
      puts("Wrong password!");
    }
  }
  else {
    puts("Wrong code!");
  }
  if (local_10 == *(long *)(in_FS_OFFSET + 0x28)) {
    return 0;
  }
                    /* WARNING: Subroutine does not return */
  __stack_chk_fail();
}
