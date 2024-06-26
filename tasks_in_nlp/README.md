# Задача 2
## Аудио модели – по генерации и синтезу речи
### Задача автоматического распознавания речи (ASR)
Решение задачи ASR выполнено на базе модели `WISPER`

`Whisper` - это предварительно обученная модель для автоматического распознавания речи (ASR) и перевода речи. Модели `Whisper`, обученные на 680 тысячах часов работы с маркированными данными, демонстрируют высокую способность к обобщению для многих наборов данных и областей, `без необходимости тонкой настройки`.

`Whisper` - это модель кодировщика-декодера на основе `Transformers`, также называемая последовательной моделью. Она была обучен на 680 тысячах часов помеченных речевых данных, аннотированных с использованием крупномасштабного слабого наблюдения.

Контрольные точки `Whisper` выпускаются в пяти конфигурациях различных размеров модели (`tiny`, `base`, `small`, `medium`, `large`). Четыре самых маленьких обучаются либо только английским, либо многоязычным данным. Самые большие контрольные точки работают только на нескольких языках. Все предварительно подготовленные контрольные точки доступны на [Hugging Face Hub](https://huggingface.co/openai/whisper-large).

Модели обучались либо на данных только на английском языке, либо на многоязычных данных. Модели только на английском языке обучались задаче распознавания речи. Многоязычные модели обучались как распознаванию речи, так и переводу речи. Для распознавания речи модель предсказывает транскрипцию на том же языке, что и аудиозапись. Для перевода речи модель предсказывает транскрипцию на язык, отличный от аудиозаписи.

`Whisper` была предложена в статье [Robust Speech Recognition via Large-Scale Weak Supervision:](https://arxiv.org/abs/2212.04356) Алеком Рэдфордом и другими из OpenAI.

Репозиторий исходного кода модели находится [здесь](https://github.com/openai/whisper). 

Для практической реализации задачи была выбрана библиотека [SpeechRecognition](https://pypi.org/project/SpeechRecognition/). Это библиотека для выполнения распознавания речи с поддержкой нескольких движков и API, онлайн и офлайн, в частности она предоставляет API для подключения модели `Whisper`.

### Задача синтеза речи (TTS)

Для реализации задачи синтеза речи мы взяли предобученную модель `VITS`, которая в дальнейшем была дообучена на русскоязычных данных.
Выбранная нами Модель преобразования текста в речь с несколькими динамиками для русского языка представлена на [Hugging Face Hub](https://huggingface.co/utrobinmv/tts_ru_free_hf_vits_high_multispeaker). 

Она работает с обычным текстом с разделением знаков препинания и не требует предварительного преобразования текста в фонемы. Модель с несколькими динамиками имеет два голоса: `0 - женский`, `1 - мужской`.

Размер модели составляет 39.9 миллионов параметров, есть младшая версия с количеством параметров 15.1 миллион.

Текст может быть написан строчными буквами.

Модель обучена самостоятельно расставлять акценты. Но для повышения качества генерации мы дополнительно расставляем акценты в тексте перед гласными буквами с помощью библиотеки `ruaccent`.

### Интрефейс чат-бота
Для презентации разработан интерфейс чат бота на фреймворке `DASH`
