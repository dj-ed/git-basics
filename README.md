# git-basics
### SSH
@todo 

### GIT

https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud


Osnovni koraci kloniranja projekta
```
git clone $URL ./folder_name

cd folder_name

git status
```
Treba napomenuti da `git status` nam pokazuje status trenutnog git repoa, tj: granu na kojoj smo, izmenjene fajlove, tracked/untracked i sl.



##### U svakodnevnom poslu kada više developera radi na istom projektu retko kad radimo sa `master` granom. Uglavnom je 
```
git checkout develop
git pull origin develop
```

### Kreiranje nove grane prema $TASK_ID
```
git checkout -b feature/$TASK_ID
```
Cesto se koriste i ovi nazivi:
 - _bugfix/*_
 - _hotfix/*_

#### Brisanje grane
	- local:                `git branch -D feature/$TASK_ID`
	- upstream(na serveru): `git push origin :feature/$TASK_ID`

### Nakon odradjenih izmena na fajlovima  unutar git repo-a/projekt-a redosled komandi je u 99% slučajeva sledeci:
```
git status
git add $FILE
git commit -m "$TASK_ID $MESSAGE"
git push origin feature/$TASK_ID
git pull origin master

### RESOLVE MERGE CONFLICTS

git commit -m "Resolved merge conglicts."
git push origin feature/$TASK_ID
```


##############################################################
#### FULL Description + tips/tricks
http://www-cs-students.stanford.edu/~blynn/gitmagic/ch02.html
##############################################################

##### Example: Instant Publishing(taken from link above)

Suppose you’ve written a script you’d like to share with others. You could just tell them to download from your computer, but if they do so while you’re improving the script or making experimental changes, they could wind up in trouble. Of course, this is why release cycles exist. Developers may work on a project frequently, but they only make the code available when they feel it is presentable.

To do this with Git, in the directory where your script resides:
```
git init
git add .
git commit -m "First release"
```
Then tell your users to run:
```
git clone your.computer:/path/to/script
```
to download your script. This assumes they have ssh access. If not, run git daemon and tell your users to instead run:
```
git clone git://your.computer/path/to/script
```
From now on, every time your script is ready for release, execute:

```
git commit -am "Next release"
```
and your users can upgrade their version by changing to the directory containing your script and typing:
```
git pull
```
Your users will never end up with a version of your script you don’t want them to see.
