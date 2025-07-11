<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f12faf55ab620aef9f6761679b7ac68b",
  "translation_date": "2025-05-19T12:40:23+00:00",
  "source_file": "00-course-setup/SETUP.md",
  "language_code": "ru"
}
-->
# Настройка вашей среды разработки

Мы настроили этот репозиторий и курс с помощью [контейнера разработки](https://containers.dev?WT.mc_id=academic-105485-koreyst), который поддерживает универсальную среду выполнения для разработки на Python3, .NET, Node.js и Java. Связанная конфигурация определяется в файле `devcontainer.json`, расположенном в папке `.devcontainer/` в корне этого репозитория.

Чтобы активировать контейнер разработки, запустите его в [GitHub Codespaces](https://docs.github.com/en/codespaces/overview?WT.mc_id=academic-105485-koreyst) (для облачной среды выполнения) или в [Docker Desktop](https://docs.docker.com/desktop/?WT.mc_id=academic-105485-koreyst) (для локальной среды выполнения). Прочитайте [эту документацию](https://code.visualstudio.com/docs/devcontainers/containers?WT.mc_id=academic-105485-koreyst) для получения более подробной информации о работе контейнеров разработки в VS Code.

> [!TIP]  
> Мы рекомендуем использовать GitHub Codespaces для быстрого старта с минимальными усилиями. Он предоставляет щедрую [бесплатную квоту использования](https://docs.github.com/billing/managing-billing-for-github-codespaces/about-billing-for-github-codespaces#monthly-included-storage-and-core-hours-for-personal-accounts?WT.mc_id=academic-105485-koreyst) для личных аккаунтов. Настройте [тайм-ауты](https://docs.github.com/codespaces/setting-your-user-preferences/setting-your-timeout-period-for-github-codespaces?WT.mc_id=academic-105485-koreyst), чтобы остановить или удалить неактивные рабочие пространства и максимизировать использование вашей квоты.

## 1. Выполнение заданий

Каждый урок может содержать _необязательные_ задания, которые могут быть предоставлены на одном или нескольких языках программирования, включая: Python, .NET/C#, Java и JavaScript/TypeScript. В этом разделе приводятся общие рекомендации по выполнению этих заданий.

### 1.1 Задания на Python

Задания на Python предоставляются либо в виде приложений (файлы `.py`), либо в виде блокнотов Jupyter (файлы `.ipynb`).
- Чтобы запустить блокнот, откройте его в Visual Studio Code, затем нажмите _Select Kernel_ (вверху справа) и выберите опцию по умолчанию Python 3. Теперь вы можете нажать _Run All_, чтобы выполнить блокнот.
- Чтобы запустить приложения Python из командной строки, следуйте инструкциям, специфичным для задания, чтобы убедиться, что вы выбрали правильные файлы и предоставили необходимые аргументы.

## 2. Настройка провайдеров

Задания **могут** быть настроены для работы с одним или несколькими развертываниями моделей на основе больших языковых моделей (LLM) через поддерживаемого поставщика услуг, такого как OpenAI, Azure или Hugging Face. Они предоставляют _хостируемую конечную точку_ (API), к которой мы можем получить программный доступ с правильными учетными данными (ключ API или токен). В этом курсе мы обсуждаем этих провайдеров:

- [OpenAI](https://platform.openai.com/docs/models?WT.mc_id=academic-105485-koreyst) с разнообразными моделями, включая основную серию GPT.
- [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/?WT.mc_id=academic-105485-koreyst) для моделей OpenAI с акцентом на готовность к использованию в корпоративной среде.
- [Hugging Face](https://huggingface.co/docs/hub/index?WT.mc_id=academic-105485-koreyst) для моделей с открытым исходным кодом и сервера вывода.

**Вам потребуется использовать свои собственные аккаунты для этих упражнений**. Задания необязательны, поэтому вы можете выбрать настройку одного, всех или ни одного из провайдеров в зависимости от ваших интересов. Некоторые рекомендации по регистрации:

| Регистрация | Стоимость | Ключ API | Песочница | Комментарии |
|:---|:---|:---|:---|:---|
| [OpenAI](https://platform.openai.com/signup?WT.mc_id=academic-105485-koreyst)| [Цены](https://openai.com/pricing#language-models?WT.mc_id=academic-105485-koreyst)| [На основе проекта](https://platform.openai.com/api-keys?WT.mc_id=academic-105485-koreyst) | [Без кода, веб](https://platform.openai.com/playground?WT.mc_id=academic-105485-koreyst) | Доступно несколько моделей |
| [Azure](https://aka.ms/azure/free?WT.mc_id=academic-105485-koreyst)| [Цены](https://azure.microsoft.com/pricing/details/cognitive-services/openai-service/?WT.mc_id=academic-105485-koreyst)| [Быстрый старт SDK](https://learn.microsoft.com/azure/ai-services/openai/quickstart?WT.mc_id=academic-105485-koreyst)| [Быстрый старт Studio](https://learn.microsoft.com/azure/ai-services/openai/quickstart?WT.mc_id=academic-105485-koreyst) |  [Необходимо подать заявку заранее для доступа](https://learn.microsoft.com/azure/ai-services/openai/?WT.mc_id=academic-105485-koreyst)|
| [Hugging Face](https://huggingface.co/join?WT.mc_id=academic-105485-koreyst) | [Цены](https://huggingface.co/pricing) | [Токены доступа](https://huggingface.co/docs/hub/security-tokens?WT.mc_id=academic-105485-koreyst) | [Hugging Chat](https://huggingface.co/chat/?WT.mc_id=academic-105485-koreyst)| [Hugging Chat имеет ограниченные модели](https://huggingface.co/chat/models?WT.mc_id=academic-105485-koreyst) |
| | | | | |

Следуйте указаниям ниже, чтобы _настроить_ этот репозиторий для использования с различными провайдерами. Задания, требующие определенного провайдера, будут содержать один из следующих тегов в имени файла:
- `aoai` - требуется конечная точка Azure OpenAI, ключ
- `oai` - требуется конечная точка OpenAI, ключ
- `hf` - требуется токен Hugging Face

Вы можете настроить одного, ни одного или всех провайдеров. Связанные задания просто выдадут ошибку при отсутствии учетных данных.

### 2.1. Создайте файл `.env`

Мы предполагаем, что вы уже прочитали руководство выше и зарегистрировались у соответствующего провайдера, а также получили необходимые учетные данные для аутентификации (API_KEY или токен). В случае Azure OpenAI мы предполагаем, что у вас также есть действующее развертывание службы Azure OpenAI (конечная точка) с развернутой хотя бы одной моделью GPT для завершения чата.

Следующим шагом будет настройка ваших **локальных переменных окружения** следующим образом:

1. Найдите в корневой папке файл `.env.copy`, который должен содержать следующее:

   ```bash
   # OpenAI Provider
   OPENAI_API_KEY='<add your OpenAI API key here>'

   ## Azure OpenAI
   AZURE_OPENAI_API_VERSION='2024-02-01' # Default is set!
   AZURE_OPENAI_API_KEY='<add your AOAI key here>'
   AZURE_OPENAI_ENDPOINT='<add your AOIA service endpoint here>'
   AZURE_OPENAI_DEPLOYMENT='<add your chat completion model name here>' 
   AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT='<add your embeddings model name here>'

   ## Hugging Face
   HUGGING_FACE_API_KEY='<add your HuggingFace API or token here>'
   ```

2. Скопируйте этот файл в `.env`, используя команду ниже. Этот файл _gitignore-д_, чтобы сохранить секреты в безопасности.

   ```bash
   cp .env.copy .env
   ```

3. Заполните значения (замените заполнители справа от `=`) как описано в следующем разделе.

3. (Опция) Если вы используете GitHub Codespaces, у вас есть возможность сохранить переменные окружения как _секреты Codespaces_, связанные с этим репозиторием. В этом случае вам не нужно будет настраивать локальный .env файл. **Однако обратите внимание, что эта опция работает только в случае использования GitHub Codespaces.** Вам все равно нужно будет настроить .env файл, если вы используете Docker Desktop.

### 2.2. Заполнение файла `.env`

Давайте быстро рассмотрим имена переменных, чтобы понять, что они представляют:

| Переменная  | Описание  |
| :--- | :--- |
| HUGGING_FACE_API_KEY | Это токен доступа пользователя, который вы настроили в своем профиле |
| OPENAI_API_KEY | Это ключ авторизации для использования сервиса для не-Azure OpenAI конечных точек |
| AZURE_OPENAI_API_KEY | Это ключ авторизации для использования этого сервиса |
| AZURE_OPENAI_ENDPOINT | Это развернутая конечная точка для ресурса Azure OpenAI |
| AZURE_OPENAI_DEPLOYMENT | Это конечная точка развертывания модели _генерации текста_ |
| AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT | Это конечная точка развертывания модели _встраивания текста_ |
| | |

Примечание: последние две переменные Azure OpenAI отражают модель по умолчанию для завершения чата (генерации текста) и поиска вектора (встраивания) соответственно. Инструкции по их настройке будут определены в соответствующих заданиях.

### 2.3 Настройка Azure: из портала

Значения конечной точки и ключа Azure OpenAI можно найти в [Azure Portal](https://portal.azure.com?WT.mc_id=academic-105485-koreyst), поэтому начнем с этого.

1. Перейдите в [Azure Portal](https://portal.azure.com?WT.mc_id=academic-105485-koreyst)
1. Нажмите на опцию **Ключи и конечная точка** в боковой панели (меню слева).
1. Нажмите **Показать ключи** - вы должны увидеть следующее: КЛЮЧ 1, КЛЮЧ 2 и Конечная точка.
1. Используйте значение КЛЮЧ 1 для AZURE_OPENAI_API_KEY
1. Используйте значение конечной точки для AZURE_OPENAI_ENDPOINT

Теперь нам нужны конечные точки для конкретных моделей, которые мы развернули.

1. Нажмите на опцию **Развертывания моделей** в боковой панели (меню слева) для ресурса Azure OpenAI.
1. На целевой странице нажмите **Управление развертываниями**

Это приведет вас на сайт Azure OpenAI Studio, где мы найдем другие значения, как описано ниже.

### 2.4 Настройка Azure: из Studio

1. Перейдите в [Azure OpenAI Studio](https://oai.azure.com?WT.mc_id=academic-105485-koreyst) **из вашего ресурса**, как описано выше.
1. Нажмите на вкладку **Развертывания** (боковая панель, слева), чтобы просмотреть текущие развернутые модели.
1. Если ваша желаемая модель не развернута, используйте **Создать новое развертывание**, чтобы развернуть ее.
1. Вам понадобится модель _генерации текста_ - мы рекомендуем: **gpt-35-turbo**
1. Вам понадобится модель _встраивания текста_ - мы рекомендуем **text-embedding-ada-002**

Теперь обновите переменные окружения, чтобы отразить _Имя развертывания_, используемое. Это обычно будет то же самое, что и имя модели, если вы не изменили его явно. Итак, например, у вас может быть:

```bash
AZURE_OPENAI_DEPLOYMENT='gpt-35-turbo'
AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT='text-embedding-ada-002'
```

**Не забудьте сохранить файл .env после завершения**. Теперь вы можете выйти из файла и вернуться к инструкциям по запуску блокнота.

### 2.5 Настройка OpenAI: из профиля

Ваш ключ API OpenAI можно найти в вашем [аккаунте OpenAI](https://platform.openai.com/api-keys?WT.mc_id=academic-105485-koreyst). Если у вас его нет, вы можете зарегистрироваться и создать ключ API. Как только у вас будет ключ, вы можете использовать его для заполнения переменной `OPENAI_API_KEY` в файле `.env`.

### 2.6 Настройка Hugging Face: из профиля

Ваш токен Hugging Face можно найти в вашем профиле в разделе [Токены доступа](https://huggingface.co/settings/tokens?WT.mc_id=academic-105485-koreyst). Не публикуйте и не делитесь ими публично. Вместо этого создайте новый токен для использования в этом проекте и скопируйте его в файл `.env` в переменную `HUGGING_FACE_API_KEY`. _Примечание:_ Это технически не ключ API, но используется для аутентификации, поэтому мы сохраняем это наименование для согласованности.

**Отказ от ответственности**:  
Этот документ был переведен с помощью службы автоматического перевода [Co-op Translator](https://github.com/Azure/co-op-translator). Хотя мы стремимся к точности, пожалуйста, учитывайте, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его родном языке следует считать авторитетным источником. Для критически важной информации рекомендуется профессиональный перевод человеком. Мы не несем ответственности за любые недоразумения или неправильные интерпретации, возникающие в результате использования этого перевода.