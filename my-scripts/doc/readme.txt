1) create a new repo on github

2) add my-scripts dir

cd meta-mender

echo "# meta-mender fork" >> README.md

git init

git add .

git commit -m "first commit"

git remote add origin git@github.com:RobertBerger/meta-mender.git

git push -u origin master

3) use my repo

mv meta-mender meta-mender.ori
git clone git://github.com/RobertBerger/meta-mender.git

4) add upstream

cd meta-mender

git remote add official-upstream git://github.com/mendersoftware/meta-mender

git fetch official-upstream

git branch -a

5) use specific upstream branch/commit and make own branch

syntax: git fetch url-to-repo branchname:refs/remotes/origin/branchname

git fetch git://github.com/mendersoftware/meta-mender thud:refs/remotes/origin/thud

6) Update from upstream:
git co master
>> git remote -v

official-upstream       git://github.com/mendersoftware/meta-mender (fetch)
official-upstream       git://github.com/mendersoftware/meta-mender (push)
origin  git://github.com/RobertBerger/meta-mender.git (fetch)
origin  git://github.com/RobertBerger/meta-mender.git (push)


>> git fetch official-upstream
---

7) My own branch:
git co master
git co official-upstream/thud
git checkout -b 2019-09-10-thud-as-warrior
git co master
./my-scripts/push-all-to-github.sh

8) apply patches

cd meta-mender

git co 2019-09-10-thud-as-warrior

stg init

stg series

stg import --mail ../meta-mender-patches/2019-09-10-thud-as-warrior/0001-use-systemd-as-cgroup-manager-for-docker-While-it-s-.patch

import all patches

...

stg series 

stg commit --all

git log

git co master

9) push to my upstream

my-scripts/push-all-to-github.sh

