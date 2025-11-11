```
liza@INBOOKX3Plus:~$ mkdir lab_1
liza@INBOOKX3Plus:~$ cd lab_1
liza@INBOOKX3Plus:~/lab_1$ git clone https://github.com/ZabaraLiza2005/lab
Cloning into 'lab'...
remote: Enumerating objects: 30, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (20/20), done.
remote: Total 30 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (30/30), 7.18 KiB | 253.00 KiB/s, done.
liza@INBOOKX3Plus:~/lab_1$ cd lab
liza@INBOOKX3Plus:~/lab_1/lab$ cd starter_repo
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ docker compose up -d --build

The command 'docker' could not be found in this WSL 2 distro.
We recommend to activate the WSL integration in Docker Desktop settings.

For details about using Docker Desktop with WSL 2, visit:

https://docs.docker.com/go/wsl2/

liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ docker compose up -d --build
[+] Running 1/1
 ✔ Container starter_repo-app-1  Started                                                                           1.2s
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ docker compose exec app python -m pytest -q
...                                                                                                              [100%]
3 passed in 0.01s
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git config --global user.name ZabaraLiza2005
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git config --global user.email sharimzastil@gmail.com
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ gpg --list-secret-keys --keyid-format=long
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
/home/liza/.gnupg/pubring.kbx
-----------------------------
sec   rsa2048/F86392DA2127F1B7 2025-11-01 [SC]
      A1358EEABF751E86850EF7AEF86392DA2127F1B7
uid                 [ultimate] ZabaraLiza2005 <sharimzastil@gmail.com>

liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git config --global user.signingkey A1358EEABF751E86850EF7AEF86392DA2127F1B7
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git config --global commit.gpgsign true
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git checkout -b feature/setup
Switched to a new branch 'feature/setup'
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git fetch origin && git rebase origin/main
Current branch feature/setup is up to date.
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git add .
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git commit -m
error: switch `m' requires a value
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git commit -m "ok"
error: gpg failed to sign the data
fatal: failed to write commit object
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git commit -m "ok"
[feature/setup 870b97e] ok
 5 files changed, 23 insertions(+), 37 deletions(-)
 create mode 100644 starter_repo/app/__pycache__/__init__.cpython-311.pyc
 create mode 100644 starter_repo/app/__pycache__/calc.cpython-311.pyc
 rewrite starter_repo/scripts/bisect_demo_init.sh (79%)
 create mode 100644 starter_repo/tests/__pycache__/test_calc.cpython-311-pytest-7.4.4.pyc
 create mode 100644 starter_repo/tests/__pycache__/test_smoke.cpython-311-pytest-7.4.4.pyc
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ bash scripts/bisect_demo_init.sh
[feature/setup 59d6502] [demo] add calc_good.py
 1 file changed, 6 insertions(+)
 create mode 100644 starter_repo/app/calc_good.py
[feature/setup 8ef733e] [demo] introduce bug
 1 file changed, 2 insertions(+), 4 deletions(-)
[ok] created tag good_baseline and bad HEAD
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git bisect start
You need to run this command from the toplevel of the working tree.
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ git bisect start
You need to run this command from the toplevel of the working tree.
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ cd -
/home/liza/lab_1/lab
liza@INBOOKX3Plus:~/lab_1/lab$ git bisect start
liza@INBOOKX3Plus:~/lab_1/lab$ git bisect bad HEAD
liza@INBOOKX3Plus:~/lab_1/lab$ git bisect good good_baseline
8ef733e1efd61762946da57e45f969b7f9a889a2 is the first bad commit
commit 8ef733e1efd61762946da57e45f969b7f9a889a2
Author: ZabaraLiza2005 <sharimzastil@gmail.com>
Date:   Tue Nov 11 14:08:35 2025 +0600

    [demo] introduce bug

 starter_repo/app/calc.py | 6 ++----
 1 file changed, 2 insertions(+), 4 deletions(-)
```
```
liza@INBOOKX3Plus:~/lab_1/lab$ pre-commit install
pre-commit installed at .git/hooks/pre-commit
liza@INBOOKX3Plus:~/lab_1/lab$ pre-commit -a
usage: pre-commit [-h] [-V]
                  {autoupdate,clean,gc,init-templatedir,install,install-hooks,migrate-config,run,sample-config,try-repo,uninstall,validate-config,validate-manifest,help,hook-impl}
                  ...
pre-commit: error: unrecognized arguments: -a
liza@INBOOKX3Plus:~/lab_1/lab$ pre-commit run  -a
An error has occurred: InvalidConfigError:
=====> .pre-commit-config.yaml is not a file
Check the log at /home/liza/.cache/pre-commit/pre-commit.log
liza@INBOOKX3Plus:~/lab_1/lab$ cd starter_repo
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ touch .pre-commit-config.yaml
liza@INBOOKX3Plus:~/lab_1/lab/starter_repo$ pre-commit run -a
trim trailing whitespace.................................................Passed
fix end of files.........................................................Failed
- hook id: end-of-file-fixer
- exit code: 1
- files were modified by this hook

Fixing starter_repo/app/__init__.py
Fixing starter_repo/scripts/mini-smoke.sh
Fixing starter_repo/compose.yaml
Fixing starter_repo/docs/adr/templates/adr-template.md
Fixing starter_repo/README.md
Fixing starter_repo/app/calc_buggy.py
Fixing starter_repo/scripts/bisect_test.sh
Fixing starter_repo/tests/test_calc.py
Fixing starter_repo/scripts/bisect_demo_init.sh
Fixing starter_repo/app/calc_good.py
Fixing starter_repo/app/calc.py
Fixing starter_repo/tests/test_smoke.py
Fixing starter_repo/docs/adr/README.md
Fixing starter_repo/requirements.txt

check yaml...............................................................Passed
check json...........................................(no files to check)Skipped
check for added large files..............................................Passed
```
