# Library Project — გაშვების ინსტრუქცია (Windows / VS Code)

## 1. გახსნა
1. ჩამოტვირთეთ ZIP და ამოარქივეთ (Extract All ან WinRAR → Extract Here).
2. VS Code-ში აირჩიეთ **File → Open Folder...** და გახსენით `library_project_ready` საქაღალდე.
3. VS Code-ში გახსენით ტერმინალი: **Terminal → New Terminal**.

## 2. ვირტუალური გარემო და Django
ტერმინალში, პროექტის მთავარ საქაღალდეში (სადაც `manage.py` დევს), შეასრულეთ სათითაოდ:

```bat
python -m venv myenv
myenv\Scripts\activate.bat
python -m pip install -r requirements.txt
```

თუ PowerShell-ში `activate.bat` არ გაეშვა, გამოიყენეთ:
```powershell
.\myenv\Scripts\Activate.ps1
```
თუ PowerShell სკრიპტის გაშვებას კრძალავს, გამოიყენეთ VS Code-ის Command Prompt ტერმინალი ან CMD.

## 3. მონაცემთა ბაზის მომზადება და სერვერის გაშვება
```bat
python manage.py migrate
python manage.py runserver
```

ტერმინალში გამოჩნდება მისამართი. ბრაუზერში გახსენით:
**http://127.0.0.1:8000/**

წიგნების გვერდი:
**http://127.0.0.1:8000/books/**

სერვერის გასაჩერებლად ტერმინალში დააჭირეთ `Ctrl + C`.

## 4. რა სად არის
- `library_project/settings.py` — Django-ს პარამეტრები; `library_app` უკვე დამატებულია `INSTALLED_APPS`-ში.
- `library_project/urls.py` — მთავარი მისამართები; აპის მისამართები ჩართულია `include()`-ით.
- `library_app/views.py` — გვერდების ფუნქციები და წიგნების სია.
- `library_app/urls.py` — აპის URL-ები.
- `library_app/templates/` — HTML შაბლონები: `base.html`, `home.html`, `books.html`.
- `library_app/static/library_app/style.css` — გვერდების დიზაინი.

## 5. წიგნების შეცვლა
გახსენით `library_app/views.py` და `books` სიაში შეცვალეთ წიგნის `title` ან `pages`.
`pages > 300` შემთხვევაში გვერდზე გამოჩნდება „გრძელი წიგნია“, სხვა შემთხვევაში — „მოკლე წიგნია“.

შენიშვნა: `myenv` საქაღალდე ZIP-ში არ დევს — ის თქვენს კომპიუტერზე ზემოთ მოცემული ბრძანებებით შეიქმნება.

## განახლებული წიგნების კატალოგი
`library_app/views.py`-ში თითოეულ წიგნს აქვს ავტორი, აღწერა, ჟანრი, გვერდების რაოდენობა და ყდის სურათის მისამართი.
ყდის ილუსტრაციები პროექტში ლოკალურად ინახება: `library_app/static/library_app/covers/`.
სურათების სანახავად ინტერნეტი საჭირო არ არის. ახალი წიგნის დასამატებლად დაამატეთ ახალი ობიექტი `books` სიაში და მოათავსეთ მისი SVG/JPG/PNG ყდა იმავე `covers` საქაღალდეში.
