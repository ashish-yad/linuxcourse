1] Genarate two ssh keys for using in different account, and move it to .ssh/ folder
ssh-keygen -t rsa
ssh-keygen -t rsa -C "email@work_mail.com" -f "id_rsa_work_user1"



2] Add the ssh keys into the corresponding git portal

3] add these keys to ssh-agent

eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/id_rsa_work_user1

4]modify .ssh/config in order to point to correct keys to correct host

$ cd ~/.ssh/
$ touch config           // Creates the file if not exists
$ code config            // Opens the file in VS code, use any editor

# Personal account, - the default config
Host github.com
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_rsa
   
# Work account-1
Host github.com-work_user1    
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_rsa_work_user1

5] cloning the repo
On cloning, make a note that we use the host names that we used in the SSH config.

git clone git@github.com:personal_account_name/repo_name.git
git clone git@github.com-work_user1:work_user1/repo_name.git

