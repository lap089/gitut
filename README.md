# GitHub Tutorial

## Git Basics

###  Git configuration
* Username:  
  ```git config --global user.name "Your Name"```
* E-mail:  
  ```git config --global user.email "your@email.com"```
* Editor:  
  ```
  git config --global core.editor editor-shortcut
  
  git config --global core.editor "path/to/your/edtitor"
  ```
* Get a specific configuration:  
  ```git config [field]```
* List all configrations:  
  ```git config --list```

### Git workspace setup
* Initialize current folder for Git system: (required to be an empty folder)  
  ```git init```
* Initialize a new child folder (of current one) for Git system:  
  ```git init [folder-name]```
* Clone an existing repository to current folder: (empty folder required)  
  ```git clone [repository-url]```
* Clone an existing repository to a child folder of current: (empty folder required)  
  ```git cloen [repository-url] [folder-name]```
