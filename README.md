# morphoRuEval

Код по соревнованию MorphoRuEval

Сам метод представлен в:
  - статье http://www.dialog-21.ru/media/3916/kazennikovao.pdf
  - презентации https://www.slideshare.net/kzn/morphorueval2017-partofspeech-tagging-the-power-of-the-linear-svmbased-filtration-method-for-russian-language

- Весь код экспериментальный, поэтому необходимы некоторые предварительные действия для воспроизведения результатов прогона. Все пути указаны относительно репозитория этого проекта.
  - Надо поместить весь репозиторий соревнования в директорию morphoRuEval
  - Распаковать архив ГИКРЯ (morphoRuEval/GICRYA_texts.zip) в директории morphoRuEval
  - Распаковать архив СинТагРус (morphoRuEval/SYNTAGRUS_texts.zip) в директории morphoRuEval
  - Создать файл morphoRuEval/corpus_full.txt с помощью конкатенации файлов morphoRuEval/gikrya_fixed.txt и syntagrus_full.ud
  - Распаковать тестовые данные в morphoRuEval/test
  - Создать директорию modules в корне проекта и склонировать в нее репозитории
     - https://github.com/kzn/common
     - https://github.com/kzn/fsa
     - https://github.com/kzn/ml
     - https://github.com/kzn/jaot
- Для сборки используется Gradle: https://gradle.org/
- Сборка проекта осуществляется командой: gradle dist. В результате в директории dist будут доступны jar-файлы проекта и и всех зависимостей
- После сборки можно запустить процедуру обучения и разметки тествой коллекции. Это выполняется с помощью команды java -cp dist/\* name.kazennikov.morphoRuEval.FinalTagger
- В результате все файлы с расширением .txt в директории morphoRuEval/test будут размечены
- Для чистоты прогонов построение словаря и обучение модели производится при каждом запуске
- Обучение модели предполагает наличия минимум 8Gb RAM (для обеспечения 4 Gb java-процессу) и 4 ядер, поскольку обучение идет в несколько потоков
- По времени весь прогон от обучения до разметки занимает 10-15 минут на машине Core i7 4790k, 16Gb RAM

