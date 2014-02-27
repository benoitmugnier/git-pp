git-pp
======

Git plugin to simplify workflows with git push and git pull  

Install
-------

####Move the script to the plugin directory of git:  
    cp ./git-pp /usr/bin/
    
####Set the executable mode for user:  
    chmod g+x /usr/bin/git-pp  

####Enable autocompletion (do not work with "git pp" syntax, use the alias "pp" instead):
    ~$ vim .bashrc
      alias pp='/usr/bin/git-pp'
      complete -F _git_checkout pp

Usage
-----

####Push local master to origin
    bmu@test:~/dev/project$ git pp master origin/master  
    
####Generate:  
    
    ~/dev/project$ git checkout master  
      Already on 'master'  
      Your branch is ahead of 'origin/master' by 1 commit.  
    ~/dev/project$ git merge master**  
      Already up-to-date.  
    ~/dev/project$ git push origin master**  
      Counting objects: 5, done.  
      Delta compression using up to 2 threads.  
      Compressing objects: 100% (3/3), done.  
      Writing objects: 100% (3/3), 297 bytes, done.  
      Total 3 (delta 2), reused 0 (delta 0)  
      To git@github.com:beenwa/git-pp.git  
      5451cdc..4be3acd  master -> master  
    Great Success!

####Pull dev into qa (local branchs)  
    bmu@test:~/dev/project$ git pp dev qa  

####Pull preprod/dev + Pickup COMMIT42 on local dev and push the result into origin/master  
    bmu@test:~/dev/project$ git pp preprod/dev dev:COMMIT42 origin/master  

####Merge of origin/master + worker/dev and push the result into origin/qa  
    bmu@test:~/dev/project$ git pp origin/master worker/dev origin/qa  

####Merge of origin/qa + worker/feature + pickup local dev:COMMIT42 and push the result into origin/qa  
    bmu@test:~/dev/project$ git pp origin/qa worker/feature dev:COMMIT42 origin/qa  
    
Tips
----
####Fast forward mode
Pull current branch from origin --ref (default --ref=origin) and push the result to origin.

    bmu@test:~/dev/project$ git pp --auto 
