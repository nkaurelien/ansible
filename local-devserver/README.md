

# Run

```console

ansible-playbook dev-server.yml -i localhost, --tags nvm,nodejs,git-clone -v -K

```
Option: 

- -K: Cette option invite à saisir le mot de passe à chaque exécution du playbook. 
- --ask-become-pass: Synonyme de -K.
- -v (ou --verbose) sert à augmenter le niveau de verbosité des sorties.

# Suggestions

### Additional Tools Installation:

Consider adding comments to clarify the purpose of each package group (devops-tools)

### User Management:

The password variable uses {{ ansible_user_password }}. This might not be secure depending on your setup. Consider using a password vault or a different approach for managing passwords.

### Python Package Installation:

The task uses creates to create a symlink in /usr/local/bin. This might not be ideal for system-wide installations. It's recommended to use a virtual environment for Python packages.

### Overall:

This playbook provides a good starting point for setting up a local development server in Ubuntu.  Here are some additional points to consider:

Firewall Configuration: Review the firewall rules carefully to ensure they meet your specific security needs.
Error Handling: Consider adding error handling to the tasks using the rescue keyword to handle potential issues during execution.
Customization: The playbook offers many optional features. Comment out or remove sections you don't need for your specific development environment.

> By incorporating these suggestions, you can make the playbook more robust, secure, and adaptable to your development workflow.