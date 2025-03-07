Дотримуйтесь цього посібника, щоб локально налаштувати мобільний застосунок freeCodeCamp на своїй системі. Особливо рекомендовано, якщо ви хочете робити внески регулярно.

Деякі з робочих процесів (наприклад, виправлення помилок у кодовій базі) вимагають локального запуску freeCodeCamp.

## Як підготувати локальну машину

Для початку встановіть передумовне програмне забезпечення для своєї операційної системи.

### Передумови

| Передумова                      | Версія | Примітки                                      |
| ------------------------------- | ------ | --------------------------------------------- |
| [Flutter](https://flutter.dev/) | `3.x`  | -                                             |
| Dart (разом із Flutter)         | `3.x`  | Ми використовуємо версію, з’єднану з Flutter. |

> [!ATTENTION] Якщо у вас інша версія, встановіть рекомендовану версію. Ми можемо розв’язати проблеми зі встановленням лише для рекомендованих версій.

Якщо на вашій машині вже встановлено Flutter, запустіть наступні команди для перевірки версій:

```console
flutter --version
dart --version
```

> [!TIP] Ми наполегливо рекомендуємо оновити вищевказані програмні забезпечення до останнього стабільного випуску.

Як тільки ви встановили передумови, потрібно підготувати середовище розробки. Це характерно для багатьох робочих процесів розробки, і це потрібно зробити лише один раз.

#### Виконайте наступні дії, щоб підготувати середовище розробки:

1. Встановіть [Git](https://git-scm.com/) або інший клієнт Git, якщо ви досі цього не зробили. Оновіть його до останньої версії; версія, яка пов’язана з вашою ОС, може бути застарілою.

2. Встановіть [Android Studio](https://developer.android.com/studio) та [емулятори Android](https://developer.android.com/studio/run/managing-avds) з останньою випущеною версією Android. Ми рекомендуємо використовувати Pixel 3a XL та Nexus One (для емуляції менших екранів).

3. (Додатково для MacOS) Встановіть Xcode та симулятор iOS з останньою випущеною версією iOS.

4. (Необов’язково, але рекомендовано) [Налаштуйте ключ SSH](https://help.github.com/articles/generating-an-ssh-key/) для GitHub.

5. Встановіть редактор коду на свій вибір.

   Ми наполегливо рекомендуємо використовувати [Visual Studio Code](https://code.visualstudio.com/) або Android Studio. Ми також рекомендуємо встановити офіційні [розширення](https://docs.flutter.dev/get-started/editor?tab=vscode).

## Розгалужте репозиторій на GitHub

[Розгалуження](https://help.github.com/articles/about-forks/) — це етап, на якому ви отримаєте власну копію репозиторію на GitHub.

Це дуже важливо, оскільки ви зможете працювати над власною копією мобільного застосунку freeCodeCamp на GitHub або завантажити (клонувати) репозиторій для локальної роботи. Пізніше ви зможете запропонувати внести зміни до головного репозиторію зі свого розгалуження за допомогою запиту на злиття (PR).

> [!TIP] Головний репозиторій на `https://github.com/freeCodeCamp/mobile` часто називають репозиторієм `upstream`.
> 
> Ваше розгалуження на `https://github.com/YOUR_USER_NAME/mobile` часто називають репозиторієм `origin`. `YOUR_USER_NAME` буде змінено на ваше ім’я користувача GitHub.

**Виконайте наступні кроки, щоб розгалужити репозиторій `https://github.com/freeCodeCamp/mobile`:**

1. Перейдіть до мобільного репозиторію freeCodeCamp на GitHub: <https://github.com/freeCodeCamp/mobile>

2. Натисніть кнопку «Fork» у верхньому правому куті інтерфейсу ([детальніша інформація тут](https://help.github.com/articles/fork-a-repo/))

3. Як тільки репозиторій розгалужено, вас буде переміщено до копії репозиторію на `https://github.com/YOUR_USER_NAME/mobile` (`YOUR_USER_NAME` буде змінено на ваше ім’я користувача GitHub.)

## Клонуйте розгалуження з GitHub

[Клонування](https://help.github.com/articles/cloning-a-repository/) — це **завантаження** копії репозиторію з `віддаленого` розташування, що належить вам або комусь іншому. У цьому випадку віддаленим розташуванням є ваш `fork` репозиторію freeCodeCamp, який доступний на `https://github.com/YOUR_USER_NAME/mobile`. (`YOUR_USER_NAME` буде змінено на ваше ім’я користувача GitHub.)

Запустіть ці команди на своїй локальній машині:

1. Відкрийте термінал / командний рядок / оболонку в каталозі проєктів

   _тобто `/yourprojectsdirectory/`_

2. Клонуйте своє розгалуження freeCodeCamp, замінивши `YOUR_USER_NAME` на ім’я користувача GitHub

   ```console
   git clone --depth=1 https://github.com/YOUR_USER_NAME/mobile.git
   ```

Це завантажить весь мобільний репозиторій freeCodeCamp у ваш каталог проєктів.

Зверніть увагу: `--depth=1` створює поверхневий клон вашого розгалуження, використовуючи лише останню історію/затвердження.

## Налаштуйте синхронізацію з батьківського репозиторію

Ви завантажили копію розгалуження, а отже вам потрібно налаштувати `upstream` віддалено від батьківського репозиторію.

[Як згадувалось раніше](#fork-the-repository-on-github), головний репозиторій має назву `upstream`. Розгалуження називають репозиторієм `origin`.

Вам потрібне посилання від локального клону на репозиторій `upstream` на додаток до репозиторію `origin`. Це необхідно для того, щоб ви могли синхронізувати зміни з головного репозиторію без багаторазового розгалуження і клонування.

1. Змініть каталог на новий каталог `mobile`:

   ```console
   cd mobile
   ```

2. Додайте віддалене посилання на головний репозиторій мобільного застосунку freeCodeCamp:

   ```console
   git remote add upstream https://github.com/freeCodeCamp/mobile.git
   ```

3. Переконайтеся, що конфігурація правильна:

   ```console
   git remote -v
   ```

   Вивід повинен бути схожим на нижчеподаний приклад (замініть `YOUR_USER_NAME` на своє ім’я користувача GitHub):

   ```console
   origin    https://github.com/YOUR_USER_NAME/mobile.git (fetch)
   origin    https://github.com/YOUR_USER_NAME/mobile.git (push)
   upstream    https://github.com/freeCodeCamp/mobile.git (fetch)
   upstream    https://github.com/freeCodeCamp/mobile.git (push)
   ```

## Локальний запуск мобільного застосунку freeCodeCamp

Тепер у вас є локальна копія мобільного застосунку, тому дотримуйтесь цих інструкцій для локального запуску.

Якщо у вас виникли проблеми, спочатку спробуйте знайти розв’язок в інтернеті. Якщо розв’язку немає, пошукайте його на нашій сторінці [завдань GitHub](https://github.com/freeCodeCamp/mobile/issues) та повідомте про проблему, якщо про неї ще не повідомляли.

І як завжди, не соромтесь ставити запитання [на форумі у категорії «Contributors»](https://forum.freecodecamp.org/c/contributors) або [у чаті](https://discord.gg/PRyKn3Vbay).

> [!NOTE] Каталог `mobile` містить дві папки, тобто `mobile-api` та `mobile-app`. `mobile-api` містить код API, який використовується для обслуговування подкастів. `mobile-app` містить застосунок Flutter, у якому ви повинні знаходитись під час виконання нижчеподаних кроків.

### Налаштування залежностей

#### Крок 1: налаштуйте файл змінних середовища

Ключі API та змінні середовища за замовчуванням зберігаються у файлі `sample.env`. Цей файл потрібно скопіювати в новий файл під назвою `.env`, доступ до якого відкривається динамічно на кроці встановлення. Не забудьте змінити каталог на `mobile-app` перед виконанням наступних команд.

```console
# Створіть копію «sample.env» та назвіть її «.env».
# Заповніть її необхідними ключами та секретами API:
```

#### **macOS/Linux**

```console
cp sample.env .env
```

#### **Windows**

```console
copy sample.env .env
```

Для локального запуску застосунку _необов’язково_ змінювати ключі у файлі `.env`. Ви можете залишити значення за замовчуванням, скопійовані з `sample.env`.

#### Крок 2: встановіть залежності

У цьому кроці буде встановлено залежності, необхідні для запуску застосунку:

```console
flutter pub get
```

#### Крок 3: запустіть мобільний застосунок freeCodeCamp

Запустіть емулятор (Android або iOS) та зачекайте, поки не завершиться завантаження.

Тепер ви можете запустити застосунок, виконавши наступну команду:

```console
flutter run
```

> [!TIP] Якщо ви використовуєте VSCode або Android Studio, ви можете запустити застосунок, не виконуючи жодних термінальних команд. Більше інформації [тут](https://docs.flutter.dev/get-started/test-drive).

## Введення змін локально

Тепер ви можете вносити зміни до файлів та затверджувати їх у локальному клоні розгалуження.

Дотримуйтеся цих вказівок:

1. Переконайтесь, що знаходитесь на гілці `main`:

   ```console
   git status
   ```

   Ви повинні отримати такий вивід:

   ```console
   On branch main
   Your branch is up-to-date with 'origin/main'.

   nothing to commit, working directory clean
   ```

   Якщо ви не перебуваєте на головній гілці (main) або ваш робочий каталог не чистий, розв’яжіть будь-які невиконані файли/затвердження та перевірте `main`:

   ```console
   git checkout main
   ```

2. Синхронізуйте останні зміни віддаленої гілки `main` зі своєю локальною гілкою main:

   > [!WARNING] Якщо у вас є невиконані запити на злиття, зроблені з гілки `main` свого розгалуження, ви втратите їх під кінець цього кроку.
   > 
   > Перед виконанням цього кроку потрібно переконатись, що ваш запит на злиття об’єднав модератор. Щоб уникнути цього, **ніколи** не працюйте на гілці `main`.

   Цей крок **синхронізує останні зміни** з головного репозиторію мобільного застосунку freeCodeCamp. Важливо якомога частіше перебазовувати свою гілку на останню версію `upstream/main`, щоб уникнути конфліктів пізніше.

   Оновіть свою локальну копію віддаленого репозиторію мобільного застосунку freeCodeCamp:

   ```console
   git fetch upstream
   ```

   Скиньте свою головну гілку з головною гілкою мобільного застосунку freeCodeCamp:

   ```console
   git reset --hard upstream/main
   ```

   Перемістіть свою головну гілку до джерела, щоб мати чисту історію розгалуження на GitHub:

   ```console
   git push origin main --force
   ```

   Ви можете переконатись, що ваша поточна головна гілка відповідає upstream/main, виконавши diff:

   ```console
   git diff upstream/main
   ```

   Отриманий вивід має бути порожнім.

3. Створіть нову гілку:

   Ваша локальна робоча копія буде чистою, якщо ви працюватимете на окремій гілці для кожного завдання. Ніколи не працюйте на `main`. Це забруднить вашу копію мобільного застосунку freeCodeCamp, через що, можливо, доведеться починати з нового клону чи розгалуження.

   Переконайтесь, що знаходитесь на `main` та починайте розгалуження звідси:

   ```console
   git checkout -b fix/update-guide-for-xyz
   ```

   Назва вашої гілки повинна починатись з `fix/`, `feat/`, `docs/` тощо. Не використовуйте номери завдань у гілках. Вони мають бути короткими, змістовними та унікальними.

   Декілька прикладів хороших назв гілок:

   ```md
   fix/update-challenges-for-react
   fix/update-guide-for-html-css
   fix/platform-bug-sign-in-issues
   feat/add-guide-article-for-javascript
   translate/add-spanish-basic-html
   ```

4. Відредагуйте сторінки та працюйте над кодом у своєму улюбленому текстовому редакторі.

5. Як тільки ви задоволені змінами, за бажанням запустіть мобільний додаток локально для перегляду змін.

6. Переконайтеся, що виправили помилки та перевірте форматування своїх змін.

7. Перевірте та підтвердьте файли, які оновлюєте:

   ```console
   git status
   ```

   Має з’явитись список файлів `unstaged`, які ви відредагували.

   ```console
   On branch feat/documentation
   Your branch is up to date with 'upstream/feat/documentation'.

   Changes were not staged for commit:
   (use "git add/rm <file>..." to update what will be committed)
   (use "git checkout -- <file>..." to discard changes in the working directory)

       modified:   README.md
       modified:   mobile-app/lib/main.dart
   ...
   ```

8. Проіндексуйте зміни та зробіть затвердження:

   У цьому кроці потрібно позначити лише ті файли, які редагували чи додавали самостійно. Якщо необхідно, ви можете виконати скидання та виправити файли, які не збираєтеся змінювати.

   ```console
   git add path/to/my/changed/file.ext
   ```

   Або ви можете додати всі файли `unstaged` до області тимчасового зберігання:

   ```console
   git add .
   ```

   Лише ті файли, які було переміщено до області тимчасового зберігання, будуть додані під час затвердження.

   ```console
   git status
   ```

   Вивід:

   ```console
   On branch feat/documentation
   Your branch is up to date with 'upstream/feat/documentation'.

   Changes to be committed:
   (use "git reset HEAD <file>..." to unstage)

       modified:   README.md
       modified:   mobile-app/lib/main.dart
   ```

   Тепер ви можете затвердити свої зміни, використовуючи коротке повідомлення:

   ```console
   git commit -m "fix: my short commit message"
   ```

   Декілька прикладів:

   ```md
   fix: update guide article for Java - for loop
   feat: add guide article for alexa skills
   ```

   Додатково:

   Ми наполегливо рекомендуємо створювати загальноприйняті повідомлення затверджень. Це хороша практика, яку можна помітити на деяких популярних репозиторіях з відкритим кодом. Це спонукає дотримуватись стандартних практик.

   Декілька прикладів хороших повідомлень затверджень:

   ```md
   fix: update HTML guide article
   fix: update build scripts for Travis-CI
   feat: add article for JavaScript hoisting
   docs: update contributing guidelines
   ```

   Пишіть їх короткими, не більше 50 символів. Додаткову інформацію можна додати в описі затвердження.

   Це не займе більше часу ніж нестандартне повідомлення (наприклад, «update file» чи «add index.md»)

   Ви можете дізнатись більше, чому потрібно використовувати загальноприйнятні затвердження, [тут](https://www.conventionalcommits.org/en/v1.0.0-beta.2/#why-use-conventional-commits).

9. Якщо вам потрібно відредагувати файл або оновити повідомлення після створення затвердження, це можна зробити після редагування файлів за допомогою:

   ```console
   git commit --amend
   ```

   Це відкриє текстовий редактор за замовчуванням (наприклад, `nano` або `vi`), де можна редагувати заголовок повідомлення та додавати/редагувати опис.

10. Тепер надішліть свої зміни до розгалуження:

    ```console
    git push origin branch/name-here
    ```

## Запуск тестів навчальної програми мобільного застосунку

> [!NOTE] Дотримуйтесь цього розділу, якщо змінюєте тестер завдань у мобільному застосунку. В іншому випадку перейдіть до наступного розділу [як відкрити запит на злиття](#proposing-a-pull-request-pr).

1. Клонуйте копію [репозиторію freeCodeCamp](https://github.com/freeCodeCamp/freeCodeCamp) локально зі своєї локальної копії репозиторію мобільного застосунку freeCodeCamp. Структура файлів має виглядати так:

    ```console
    ├── freeCodeCamp
    ├── mobile
    ```

2. Змініть каталог на репозиторій freeCodeCamp:

    ```console
    cd freeCodeCamp
    ```

3. Make a copy of the `.env` file:

    #### **macOS/Linux**

    ```console
    cp sample.env .env
    ```

    #### **Windows**

    ```console
    copy sample.env .env
    ```

4. Install the dependencies for the freeCodeCamp repo:

    ```console
    pnpm install && pnpm run create:shared
    ```

5. Generate the challenge data JSON file:

    ```console
    pnpm run build:curriculum
    ```

6. Copy the generated JSON file to the mobile app:

    #### **macOS/Linux**

    ```console
    cp ./shared/config/curriculum.json ../mobile/mobile-app/curriculum.json
    ```

    #### **Windows**
    ```console
    copy .\config\curriculum.json ..\mobile\mobile-app\curriculum.json
    ```

7. Change directory to the mobile app:

    ```console
    cd ../mobile/mobile-app
    ```

8. Install the dependencies for the mobile app:

    ```console
    flutter pub get
    ```

9. Update the test file to use the challenge data JSON file:

    ```console
    sed -i '' 's/..\/..\/config\/curriculum.json/.\/curriculum.json/g' test/widget_test.dart
    ```

10. Generate the challenge files:

    ```console
    flutter test test/widget_test.dart
    ```

11. Start a local server to serve the challenge files with the help of `serve` package:

    ```console
    npx serve
    ```

12. In a different terminal go back to the freeCodeCamp repo:

    ```console
    cd ../../freeCodeCamp
    ```

13. Run the cypress tests:

    ```console
    pnpm cypress run --config retries=1,screenshotOnRunFailure=false,video=false,baseUrl=http://localhost:3000/generated-tests/,specPattern=cypress/e2e/mobile-learn/test-challenges.js -s cypress/e2e/mobile-learn/test-challenges.js -b chrome
    ```

## Запропонуйте запит на злиття (PR)

Як тільки ви затвердили свої зміни, див. [як відкрити запит на злиття](how-to-open-a-pull-request.md).

<!-- ## Quick commands reference - NEED TO DISCUSS ABOUT THIS

A quick reference to the commands that you will need when working locally.

| command                                                        | description                                                                         |
| -------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `npm ci`                                                       | Installs / re-install all dependencies and bootstraps the different services.       |
| `npm run seed`                                                 | Parses all the challenge markdown files and inserts them into MongoDB.              | -->

## Розв’язання проблем розробки

### Проблеми з встановленням рекомендованих попередніх умов

Ми регулярно використовуємо найновіші та найпопулярніші операційні системи, як-от macOS 10.15 і вище, Ubuntu 18.04 і вище та Windows 10 (із WSL2).

Рекомендовано шукати розв’язок певної проблеми у Google, Stack Overflow та Stack Exchange. Ймовірно, хтось вже стикався із тією ж проблемою і на ваш запит вже є відповідь.

Якщо ви використовуєте іншу ОС та/або досі стикаєтесь із проблемами, див. [отримання допомоги](#getting-help).

### Проблеми з UI, помилки збірки тощо

Якщо у вас виникли проблеми з інтерфейсом чи збіркою, може допомогти очищення:

```console
flutter clean
```

### Проблеми при встановленні залежностей

Якщо при встановленні залежностей виникають помилки, переконайтеся, що ви не перебуваєте в мережі з обмеженнями або налаштування мережевого екрана не перешкоджають доступу до ресурсів.

Перше налаштування може зайняти деякий час (залежно від пропускної здатності вашої мережі).

## Отримання допомоги

Якщо вам потрібна допомога, не соромтесь ставити питання [на нашому форумі у розділі «Contributors»](https://forum.freecodecamp.org/c/contributors) або [у чаті](https://discord.gg/PRyKn3Vbay).

У консолі вашого браузера або в Bash / терміналі / командному рядку може з’явитися помилка, яка допоможе визначити проблему. Поділіться цим повідомленням про помилку в описі проблеми, щоб іншим було легше визначити проблему і знайти рішення.
