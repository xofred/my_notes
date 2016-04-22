The public key.
```shell
cat ~/.ssh/id_rsa.pub
```

This command also works on your known_hosts file, if you want to see a list of your known hosts' ssh fingerprints. 
```shell
ssh-keygen -l -f ~/.ssh/known_hosts
```

Reference: [How do I find my RSA key fingerprint?](http://stackoverflow.com/questions/9607295/how-do-i-find-my-rsa-key-fingerprint)