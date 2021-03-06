# Подготовка текстов модулей обработки к релизу

## Терминология:
* мастер-обработка - обработка, которая передается заказчику (релиз)
* девелоп-обработка - обработка, в которой ведется разработка

## Что делает
* разбирает девелоп-обработку из исходного каталога на исходники
* в текстах модулей удаляет конструкции `#Область` и `#КонецОдласти`
* получает наименование объекта обработки
* получает версию обработки (1
* собирает мастер-обработку из исходников и дает наименование файлу обработки по шаблону:
    НаименованиеОбъектаОбработки_ВерсияОбработки.epf
* копирует мастер-обработку в целевой каталог

1 - предполагается, что версия обработки хранится в переменной `сОбработка_Версия` модуля обработки.

## Как использовать
Типовая строка запуска:
`oscript.exe autorefactor82.os КаталогДевелоп-Обработки КаталогМастер-Обработки`
где:
* КаталогДевелоп-Обработки - путь до каталога, где находится девелоп-обработка
* КаталогМастер-Обработки - путь до каталога, где храняться версии мастер-обработок

## Зависимости
* OneScript https://github.com/EvilBeaver/OneScript
* asserts - OneScript Library https://github.com/oscript-library/asserts 
* V8Reader.epf http://infostart.ru/public/106310/ обработка должна распологаться в каталоге `tools`
* v8UnPack.exe http://svn2.assembla.com/svn/V8Unpack/track/ исполняемый файл должен распологаться в каталоге `tools`
* v8files-extractor.os скрипт проекта precommit1c (https://github.com/xDrivenDevelopment/precommit1c) с небольшими изменениями брать в этом репозитарии

## Структура каталога скрипта
* \AutoRefactor
    * \tools
        * V8Reader.epf
        * v8unpack.exe
    * autorefactor82.os
    * v8files-extractor.os