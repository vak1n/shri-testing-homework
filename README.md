# Домашнее задание: автотесты

Вам дано приложение на JavaScript и нужно написать для него автотесты: интеграционные тесты на интерфейс и модульные тесты на серверную часть.

## Предметная область

Приложение отображает в браузере информацию из git репозитория: список коммитов, файловую систему для выбранного коммита, содержимое выбранного файла (поддерживаются только текстовые форматы). Для удобства навигации на каджой странице отображаются "хлебные крошки".

## Как запустить

```sh
git clone git@github.com:dima117/shri-testing-homework.git
cd shri-testing-homework
npm i
npm start
```

## Интеграционные тесты

Сценарии для интеграционных тестов

- на всех страницах (история коммитов, просмотр файловой системы, просмотр содержимого файла) правильно отображается их содержимое;
- правильно работают переходы по страницам
  - из списка коммитов на список файлов
  - из списка файлов во вложенную папку
  - из списка файлов на страницу отдельного файла
  - переходы по хлебным крошкам

## Модульные тесты

- нужно добавить в README список логических блоков системы и их сценариев
- для каждого блока нужно написать модульные тесты
- если необходимо, выполните рефакторинг, чтобы реорганизовать логические блоки или добавить точки расширения

#### Логические блоки и их сценарии (только публичные методы)

- Используем хелпер navigation
    - вызываем функцию buildFolderUrl
        - получаем url по hash, без передачи path
    - вызываем функцию buildBreadcrumbs
        - получаем крошки без параметров
        - получаем крошки по hash
        - получаем крошки по hash и path
    - вызываем функцию buildObjectUrl
        - получаем url по hash и path с предачей type = tree
        - получаем url hash и path с предачей type = blob
        - получаем url hash и path hash без type
- Используем хелпер git
    - вызываем функцию gitHistory
        - получаем ошибку Error: git log
        - получаем историю коммитов со второй позиции с лимитом два
    - вызываем функцию gitFileTree
        - получаем ошибку Error: git ls-tree
        - получаем дерево файловой системы коммита по hash
        - получаем дерево файловой системы коммита по hash и path
    - вызываем функцию gitFileContent
        - получаем ошибку Error: git show
        - получаем изменнения в коммите по hash

#### Рефакторинг

- функция buildObjectUrl перенесена в хелпер navigation