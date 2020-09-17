 - Open the Terminal in the Folder where we want to clone the git
 - Use the following command by replace your email address to generate ssh key

    ``` $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com" ```

- The use the following command to copy the generated SSH key by following command

    ``` $ pbcopy < ~/.ssh/id_rsa.pub ```

- Past the copied SSH key in

    ``` GitHub->Setting->SSH and GPG Keys ```
- Use the following command to clone git to the folder

    ``` $ git clone <git SSH URL> ```
