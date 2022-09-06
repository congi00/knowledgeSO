# C
`gcc hello.c -o hello`
`./hello`

argc parte da 1 => argv[0] è il nome del programma stesso

`int main(int argc, char* argv[]){
	if(argc != 3){
		printf("ERR! Usage: %s PID 8_CHAR_MSG\n", argv[0]);
		exit(EXIT_FAILURE);
	}
`

# Python
`import sys
import os
import magic
import subprocess

path = '.'

if (len(sys.argv) > 1): #get arguments with sys.argv
	path = sys.argv[1]


for (dirpath, dirnames, filenames) in os.walk(path): #how to access a path with os.walk
	if(dirpath == path):
		for file in filenames: #iterate through dir's files
			filep = (dirpath + '/' + file)
			if(os.access(filep, os.X_OK)): #check if a file is executable
				filetype = (magic.from_file(filep)) #get file type with magic lib
				if not ("ELF" in filetype): #check if a file is NOT an ELF 
					subprocess.call(filep, shell=True) #exec script with subprocess lib
`					
					

How to check if you're the owner of the file:
`
def ismine(path):
    return pwd.getpwuid(os.stat(path).st_uid).pw_name == os.getlogin()
`


os.path.getmtime(path)
