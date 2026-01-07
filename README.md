### Basic of Github
#### How this Repo was pushed.

```
cd /path/folder

git init

git remote add origin https://github.com/navi1910/Cheat-Sheets-V.2.git

git status

git add .

git status

git commit -m "Cheat Sheet Upload"

git checkout -b main (actually not needed)

git checkout main

git push -u origin main

```
### Python Virtual Environment
```

python -m venv myenv

myvenv\Scripts\activate

which python     # macOS or Linux
where python     # Windows

pip install numpy pandas fastapi

pip freeze > requirements.txt

python app.py

pip install ipykernel
python -m ipykernel install --user --name=myvenv

deactivate

rm -rf myvenv                                # macOS or Linux
rmdir /s myvenv                              # Windows
Remove-Item -Recurse -Force Project01_venv   # PoweShell

python -m venv myvenv
source myvenv/bin/activate   # or Windows activate
pip install -r requirements.txt

```
