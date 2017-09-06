### check

The public key.
```shell
cat ~/.ssh/id_rsa.pub
```

This command also works on your known_hosts file, if you want to see a list of your known hosts' ssh fingerprints. 
```shell
ssh-keygen -l -f ~/.ssh/known_hosts
```

### generate
```shell
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Reference: 

[How do I find my RSA key fingerprint?](http://stackoverflow.com/questions/9607295/how-do-i-find-my-rsa-key-fingerprint)

[Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)