Перед тем, как начать работу над удалённой веткой локально, необходимо получить её (fetch). Чтобы получить ветку, необходимо сделать следующее:

`git fetch origin`

Эта команда обновит все удалённые ветки. Вы сможете видеть все ветки, которые можно получить:

`git branch -v -a`

Имея список всех веток удалённого сервера, вы можете получить код необходимой ветки для редактирования, и у вас появится её локальная рабочая копия:

`git checkout -b test origin/test`