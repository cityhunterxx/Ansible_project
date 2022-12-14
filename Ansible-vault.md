# Ansible-Vault Encryption !

Can encrypt any structured data file used by Ansible. 
This can include _group_vars/_ or _host_vars/_ inventory variables, variables loaded by _include_vars_ or _vars_files_, or variable files passed on the ansible-playbook command line with _-e @file.yml_ or _-e @file.json_. Role variables and defaults are also included!

Because Ansible **tasks**, **handlers**, and other objects are data, these can also be encrypted with vault. 
If you’d like to not expose what **variables** you are using, you can keep an individual task file entirely encrypted.


# Ansible Cheat Sheet:
## Create an ansible-vault :
#Creation command :
`" $ ansible-vault create targetfile.yml"`
		⇒ New password        #Select a password for your vault
		⇒ Confirm password
		
If you : `" $ cat targetfile.yml"` You will see that the data within the Yaml file is encrypted.

## View inside the encrypted file with ansible-vault :
#Visualization command :
`" $ ansible-vault view targetfile.yml"`
	⇒ Insert your vault password for this file to see its content.

## Edit/change the ansible-vault password :
#Edit key command :
`" $ ansible-vault rekey targetfile.yml"`
		⇒ Insert your current vault password for this file 
		⇒ New password        
		⇒ Confirm password

## Encrypt a file via ansible-vault :
#Encryption command : 
`" $ ansible-vault encrypt targetfile.yml"`
		⇒ New password        #Select a password for your vault
		⇒ Confirm password
If you : `" $ cat targetfile.yml"` You will see that the data within the Yaml file is encrypted.

##  Decrypt a file via ansible-vault :
#Decryption command : 
`" $ ansible-vault decrypt targetfile.yml"`
	⇒ Insert your vault password for this file to see its content
If you : `" $ cat targetfile.yml"` You will be able to visualize or modify the data within the Yaml file.

## Edit the content of an encrypted file via ansible-vault :
#Edit key command :
`" $ ansible-vault edit targetfile.yml"`
		⇒ Insert your current vault password for this file 
		⇒ Now you can modify the content of your file 

## Ansible-playbook commands with vault : 
#Standard ansible-playbook command (there are within atleast **one encrypted file via ansible-vault** 
`" $ ansible-playbook -i inventory_name.ini playbook_name.yml --ask-become-pass --ask-vault-pass "`
In this case you will have to insert the vault password.

⇒ It is possible to store your vault password somewhere to use it while running ansible-playbook :
`" $ nano ~/.targetfile_vault"`
within the editor ⇒ just **insert your passworld** and **save** then **exit**
#ansible-playbook command with automated vault password completion :
 `" $ ansible-playbook -i inventory_name.ini playbook_name.yml --ask-become-pass --vault-password-file ~/.targetfile_vault"` # here put the path to your stored vault password 
