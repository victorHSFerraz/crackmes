int main(int argc,char **argv)

{
  char isValidPassword;
  undefined7 extraout_var;
  char password [64];
  
  printf("Welcome to Easy Crack Me");
  printf("What is the Secret ?");
  __isoc99_scanf(&DAT_00102032,password);
  isValidPassword = checkPass(password);
  if ((int)CONCAT71(extraout_var,isValidPassword) == 0) {
    printf("Better luck next time. :(");
  }
  else {
    printf("You are correct :)");
  }
  return 0;
}

/* this function iterates and check every character of the password passed. sudo0x18 is the expected
   argument */

char checkPass(char *password)

{
  char letter;
  
  if (*password == 's') {
    letter = password[1];
    if ((((letter == 'u') && (letter = password[2], letter == 'd')) &&
        (letter = password[3], letter == 'o')) &&
       (((letter = password[4], letter == '0' && (letter = password[5], letter == 'x')) &&
        ((letter = password[6], letter == '1' && (letter = password[7], letter == '8')))))) {
      letter = '\x01';
    }
  }
  else {
    letter = '\0';
  }
  return letter;
}
