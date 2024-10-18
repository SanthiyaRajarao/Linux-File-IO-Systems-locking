# Linux-File-IO-Systems-locking
Ex07-Linux File-IO Systems-locking
# AIM:
To Write a C program that illustrates files copying and locking

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux IO Systems locking

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## 1.To Write a C program that illustrates files copying 
```
#include <unistd.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <stdlib.h>
int main()
{
    char block[1024];
    int in, out;
    int nread;
    in = open("filecopy.c", O_RDONLY);
    out = open("file.out", O_WRONLY|O_CREAT, S_IRUSR|S_IWUSR);
    while((nread = read(in,block,sizeof(block))) > 0)
    write(out,block,nread);
    exit(0);}
```
## OUTPUT
![image](https://github.com/user-attachments/assets/62183812-fcd0-4315-8e00-888084804ed4)

## 2.To Write a C program that illustrates files locking
```
#include <fcntl.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <sys/file.h>
int main (int argc, char* argv[])
{
    char* file = argv[1];
    int fd;
    struct flock lock;
    printf ("opening %s\n", file);
    fd = open (file, O_WRONLY);
    if (flock(fd, LOCK_SH) == -1)
    {
        printf("error");
    }
    else
    {
        printf("Acquiring shared lock using flock");
    }
    getchar();
    if (flock(fd, LOCK_EX | LOCK_NB) == -1)
    {
        printf("error");
    }
    else
    {
        printf("Acquiring exclusive lock using flock");
    }
    getchar();
    if (flock(fd, LOCK_UN) == -1)
    {
        printf("error");
    }
    else
    {
        printf("unlocking");
    }
    getchar();
    close (fd);
    return 0;
}
```



## OUTPUT
![image](https://github.com/user-attachments/assets/15dfa774-5143-4903-8c9c-8a3a9194c760)





# RESULT:
The programs are executed successfully.
