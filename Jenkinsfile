node {
  sh 'echo hello world'
  sh 'ps -aef|grep java'
  sh '''#!/bin/bash
SOURCE_REPO=https://github.com/jenkinsci/jenkins.git
TARGET_REPO=https://github.com/gitaccountforprashant/gittest.git

git clone "${SOURCE_REPO}"
git clone "${TARGET_REPO}"

REPO_NAME=`basename "${SOURCE_REPO}" | cut -d\'.\' -f1`
TARGET_NAME=`basename "${TARGET_REPO}" | cut -d\'.\' -f1`
cd ${TARGET_NAME}
shopt -s extglob
rm -rf !(.git|.|..)
sleep 0.2
echo "---------------------------------"

cd ../${REPO_NAME}
git branch -a | grep -v HEAD | perl -ne \'chomp($_); s|^\\*?\\s*||; if (m|(.+)/(.+)| && not $d{$2}) {print qq(git branch --track $2 $1/$2\\n)} else {$d{$_}=1}\' | csh -xfs
git fetch --all
git pull --all
mv !(.git|.|..) ../${TARGET_NAME}


cd ../${TARGET_NAME}
git add --all .
git commit -m "Test commit"
git push --all origin
#git push --tags origin


cd ..
rm -rf ${REPO_NAME} ${TARGET_NAME}'''

 }
