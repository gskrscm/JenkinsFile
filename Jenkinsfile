node {
  stage 'Build and Test'
  sh '#!/bin/bashSOURCE_REPO=$1TARGET_REPO=$2git clone "${SOURCE_REPO}"git clone "${TARGET_REPO}"REPO_NAME=`basename "${SOURCE_REPO}" | cut -d\'.\' -f1`TARGET_NAME=`basename "${TARGET_REPO}" | cut -d\'.\' -f1`cd ${TARGET_NAME}shopt -s extglobrm -rf !(.git|.|..)sleep 0.2echo "---------------------------------"cd ../${REPO_NAME}git branch -a | grep -v HEAD | perl -ne \'chomp($_); s|^\\*?\\s|; if (m.+)/(.+)| && not $d{$2}) {print qq(git branch --track $2 $1/$2\\n)} else {$d{$_}=1}\' | csh -xfsgit fetch --allgit pull --allmv !(.git|.|..) ../${TARGET_NAME}cd ../${TARGET_NAME}git add --all .git commit -m "Test commit"git push --all origin#git push --tags origincd ..rm -rf ${REPO_NAME} ${TARGET_NAME}'
 }
