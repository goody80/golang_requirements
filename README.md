# golang_requirements
* If you going to build the golang with requirements(import) in the jenkins, you can use this script

## Easy to use
```
# On your golang source dir
curl -sL bit.ly/go_req | bash
```

## All Source code
```
## Have to define the WORKDIR as below
#WORKDIR="[PLEASE MAKE SURE THE WORKDIR]"
WORKDIR="./"
eval $(cat $WORKDIR/main.go | xargs 2> /dev/null | sed -e 's/^package.*.import (//g' -e 's/ ).*//g' -e $'s/ /\\\n/g' |egrep "^github" | awk '{print "go get",$1,";"}' | xargs | sed -e 's/;$//g')
```


