# cli-magic
Bash scripts, cli how-to's and other neat things in the terminal

## vshell  
Leaving poetry to uv there were some things missing. For instance 
getting into a virtual environment in sub shell. So vshell loads 
the environment and checks whether there are any .env files in the 
project root. 

Note: This only works if the  
virtual environment is localed in the .venv in your project. 
```bash
#!/bin/bash
set -o allexport 
ACTIVATE_FILE='.venv/bin/activate'
if [ -f $ACTIVATE_FILE ]; then
    if [ -f '.env' ]; then
      echo -e "👉 ENTERING A VIRTUAL ENVIRONMENT! 👈 "
      echo "💡 - found .env file! Examining 🕵️ ...."
      source '.env'
   fi
   echo "Entering sub-space shell 🚀"
   $SHELL --init-file <(cat /etc/profile ~/.bashrc "${ACTIVATE_FILE}")
   echo "Leaving 🐍 sub-shell, good bye! Love you ❤️❤️  !"
else
   echo -e "The directory doesn't seem to have an \nvirtual environment in .venv/ 😔"
fi
```
