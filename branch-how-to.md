Зачем вообще нужны ветки в гите? Для того, чтобы разделять код. Например одна ветка у нас может быть основная для разработки. Если мы делаем новый функционал, то мы создаем новую ветку под него, а после окончания работы сливаем то, что мы сделали в основную ветку.

Это дает нам возможность легко откатывать код, если вдруг мы передумаем его сливать в основную ветку, либо делать несколько различных изменений в разных ветках.

Давайте попробуем. По умолчанию в гите создается ветка мастер. На ней мы с вами все это время работали.

Если мы напишем

```git branch```

то мы увидим список всех веток, которые у нас есть. В нашем случае это только мастер. Обратите внимание на звездочку перед названием мастер. Эта звездочка показывает на какой ветке мы сейчас.

Давайте создадим новую ветку

```git branch implement-new-logic```
Если мы еще раз напишем git branch, то увидим у нас 2 ветки, но мы все еще находимся на ветке мастер. Чтобы перейти на ветку, которую мы только что создали нужно написать

```git checkout implement-new-logic```
Теперь написав git branch мы видим что мы на ветке ```implement-new-logic.```

Давайте добавим функцию getPerson в файл 2.js. Просто создадим функцию getPerson, которая будет склеивать имя и фамилию.

```function getPerson(name, surname) {
  return name + " " + surname;
}
```

сохраним и запушим наши изменения.

```git add .
git commit -m "Added getPerson function"
git push
```
Теперь если мы зайдем в наш репозиторий в браузере, то мы увидим что у нас там 2 ветки: implement-new-logic и master. Если мы перейдем на ветку implement-new-logic, то мы увидим, что на ней 5 коммитов, а в файле 2.js есть наша функция, которую мы добавили.

Если же мы перейдем обратно на мастер, для этого мы можем написать

```git checkout master```
то наши изменения, которые мы сделали так и останутся на той ветке. И пока мы их не вольем в ветку master, она не изменится.

В гите термин вливания ветки в другую ветку называется merge. Для того, что смерджить нашу ветку implement-new-logic в мастер, нам нужно сначала перейти на мастер и потом написать какую ветку мы хотим влить.

Давайте напишем

```git merge implement-new-logic```
Как мы видим, у нас написало, что ветка обновилась и добавился файл 2.js. Теперь у нас ветки стали идентичные и добавленный нами функционал находится в мастер ветке. Если мы напишем

```git log```
то увидим наш коммит, который мы добавляли на другой ветке. Так как мы ветку уже смерджили и она нам не нужна больше, давайте ее удалим.

```git branch -d implement-new-logic```
Теперь написав git branch мы опять видим только мастер. Давайте запушим эти изменения.

```git add .
git commit -m "Merged implementing new logic to master"
git push```
Теперь мы запушили наши изменения. И если мы заходим и видим master ветку, то мы видим, что у нас 5 коммитов и последним идет тот, который мы добавили. Единственное отличие в том, что мы удалили ветку локально, но не удалили ее на сервере. Вы можете зайти в список веток, all branches и нажать delete this branch. И это удаляет ветку не локально уже, а на сервере.