# Git��ʹ��

��ǩ���ո�ָ����� ���� git

---
[TOC]

1����ȡ Git�ֿ�
������Ŀ¼�г�ʼ���ֿ�
```
git init
```
ʹ��git add������ʵ�ֶ�ָ���ļ��ĸ���
```
git add *.c
git add LICENSE
git commit -m 'initial project version'
```
��¡���еĲֿ�
```
git clone https://github.com/libgit2/libgit2
```
ʹ���Զ��������
```
git clone https://github.com/libgit2/libgit2 mylibgit
```
��¼ÿ�θ��µ��ֿ�

��鵱ǰ�ļ�״̬
```
git status
On branch master
nothing to commit, working directory clean
```

�������ļ�
```
git add README
```




##1����ʼ�� git �ֿ�
```
git init
```
##2������ļ��� git �ֿ�
```
git add
git commit
```
##3����鵱ʱ�ļ�״̬
```
git status
git status -s
```
##4���鿴����
```
$ git diff     // δ add ���ݴ���
git diff HEAD �� readme.txt     // �鿴�� add �� readme.txt �ļ��� HEAD ������
```
##5���鿴��¼
```
git log
git log ��pretty=oneline
```
##6�����˰汾
```
 git reset ��hard HEAD^     // ���˵���һ�汾
 git reset ��hard HEAD~100 // ������ǰ100���汾
 git reset ��hard 2ee34     // ������ָ���汾������ʹ�� `git log` �鿴��ʷ��`git reflog` ���Բ鿴������ʷ������ȷ��Ҫ�ص�δ�����ĸ��汾��
```
##7�������޸�
###1��ֻ�޸��ˣ����ڹ�����������û�� add ���ݴ���
```
git checkout �� readme.txt     // �� ������
```
###2������Ѿ� add ���ݴ�����
```
git reset HEAD readme.txt     // ���ݴ������޸Ļ��˵�������
```
��ͬ�� git reset ��mixed HEAD readme.txt ����mixed ��Ĭ��ѡ��
```
git checkout �� readme.txt     // �������������޸�
```
###3������Ѿ��ύ
git 
##8��ɾ���ļ�
###1����С����ɾ�����ļ���rm����)
```
git checkout �� test.txt     // ���Իָ���ɾ�����ļ�����ʵ checkout ���ð汾����İ汾�滻�������İ汾�����۹��������޸Ļ���ɾ����
```
###2�������Ҫɾ���ļ�
```
git rm test.txt
git commit -m ��remove the test file"
```
##9��Զ�ֿ̲�

- ���ȴ��� ssh key
```
ssh-keygen -t rss -C ��hqp770@126.com��
```
��������쳣�������û���Ŀ¼�ҵ�.sshĿ¼�������� id_rsa �� id_rsa.pub�����ļ������������� SSH Key ����Կ�ԣ�id_rsa ��˽Կ������й¶��ȥ��id_rsa.pub �ǹ�Կ�����Ը����κ��ˡ�

- ��id_rsa.pub ��Կ��������ӵ� github ���� key ��
- ��https://github.com����Զ�ֿ̲�
������ʾ�����Խ��Լ����صĲֿ� push ��Զ�ֿ̲���
```
git remote add origin https://github.com/huangqiuping/learngit.git
git push -u origin master     // -u ����������ѱ��ص� master ��֧����������Զ���µ� master��֧������ѱ��ص� master��֧��Զ�̵�master ��֧�������������Ժ�����ͻ�����ȡʱ�Ϳ��Լ����
git push origin master     // ����ֻҪ�������޸ģ��Ϳ���ͬ����Զ��
```
##10����¡�ֿ�
```
git clone git@github.com:huangqiuping/gitskills.git
```
����
```
git clone https://github.com/huangqiuping/gitskills.git
```
Git ֧�ֶ���Э�飬���� https����ͨ�� ssh ֧�ֵ�ԭ�� git Э���ٶ���졣

##11����֧����
###1��������֧
```
git branch dev
git checkout dev
```
�������л���֧
```
git checkout -b dev
```
-b ������ʾ�������л����൱��������������
###2���鿴��֧
```
git branch // �鿴��ǰ��֧
```
###3���л���֧
```
git checkout name
```
###4���ϲ�ĳ��֧����ǰ��֧
```
git merge name     // �޷��Զ��ϲ���ʱ�򣬾���Ҫ�ֶ������ͻ��
```
###5��ɾ����֧
```
git branch -d name
```
###6���鿴��֧�ϲ����
```
git log --graph --pretty=oneline --abbrev-commit
```
###7������һ��û�кϲ����ķ�֧
```
git branch -D name
```

##12�����ص�ʱ�޸�
�������ĳһ��֧���޸�һЩ����������Ҫ��ʱ����������⣬�ֲ����ύ��ǰ���޸ģ�������ʱ���棨���أ���ǰ�޸�
```
git stash
```
�޸���󣬿���ʹ��
```
git stash pop // �ָ��ݴ��޸�
git stats list // �鿴��ʱ�ݴ�� list
```
## 13��pull&push
### 1���鿴Զ�̿���Ϣ
```
git remote -v
```
### 2���ӱ������ͷ�֧
```
git push origin branch-name���������ʧ�ܣ���ʹ��
git pull��ץȡԶ�̵����ύ
```
### 3���ڱ��ش�����Զ�̷�֧��Ӧ�ķ�֧
```
git checkout -b branch-name origin/branch-name�����ط�֧������ú�Զ��һ��
```
### 4���������ط�֧��Զ�̷�֧�Ĺ���
```
git branch ��set-upstream branch-name origin/branch-name
```
### 5����Զ��ץȡ��֧
```
git pull������г�ͻ��Ҫ�ȴ����ͻ
git mergetool  // �� merge ����
```
## 14�������������ĸ��汾�����
```
git bisect start 
git bisect good commit-id1
git bisect bad commit-id2
```
��ʱ��git�ᰴ�ն��ַ��ҳ�good�汾��bad�汾�м���Ǹ��ύ�汾�����Զ�������״̬�л����Ǹ��汾����ʱ���ǿ�����֤����汾�ǲ��������⣬��������⣬ͨ��
```
git bisect bad
```
����git����ʱgit������ҳ�һ���м�汾����������֤��ֱ�������ҳ�����ͨ��
```
git bisect good
```
����gitΪֹ��ʹ��
```
git bisect reset��������
```

## 15������ssh key
���Բο�[GitHubָ��](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
```
ssh-keygen
```

## 16��ʹ��`alias`
���ܶ�����ȡ����������`svn`����һ��������`svn commit`������Լ�дΪ`svn ci`��ʹ��`alias`���Խ�git������Ҳ�򻯣��磺
`git commit` --> `git ci`
```
git config --global alias.ci commit
git config --global alias.co checkout 
git config --global alias.st status
git config --global alias.br branch
```

�Ż���Ĳ鿴log���

```
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
```

����ʹ��`alias`�򻯣�
```
git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"
```

## 17����������
������git�����ļ�`.gitconfig`���ҵ�
```
[user]
    email = hqp770@126.com
    name = Terry
[color]
    ui = auto
[core]
    editor = vim 
[merge]
    tool = vimdiff
```



















