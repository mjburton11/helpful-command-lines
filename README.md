# helpful-command-lines

## git

* remove all branchs not on remote 
```bash
git fetch -p && git branch -vv | grep ': gone]' | awk '{print $1}' | xargs git branch -D
```

## docker

* remove all images and containers
  * kill containers `docker kill $(docker ps -q)`
  * remove containers `docker rm $(docker ps -a -q)`
  * remove images `docker rmi $(docker images -q)`

## wifi

* http://captive.apple.com

## macOS

* copy heic to jpg 
```bash
for i in *.HEIC(:r) ; sips -s format jpeg "$i.HEIC" --out "$i.jpg"
```
