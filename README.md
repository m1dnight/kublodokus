# Dependencies 

```
ansible-galaxy collection install community.general
```
# Initial Node Setup

 - Generate a local password for the users.
   ```
   export PASS=$(openssl rand -base64 10)
   echo $PASS
   ```

 - Do the initial setup of the nodes with the old sudo password. 
   **This will update to the new password!**
   ```
   ansible-playbook password.yml -f 4 --ask-become-pass --extra-vars newpassword=${PASS}
   ```
   
 - Remove the password from the bash session.
   ```
   unset PASS
   ```
 - Do the remaining initial setup. 
   ```
   ansible-playbook playbook.yml -f 4
   ```