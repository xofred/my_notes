### Command line instructions

#### Git global setup
```shell
git config --global user.name "my name"
git config --global user.email "my email"
```
#### Create a new repository
```shell
git clone repository_url
cd project_folder
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```
#### Existing folder or Git repository
```shell
cd existing_folder
git init
git remote add origin repository_url
git add .
git commit
git push -u origin master
```