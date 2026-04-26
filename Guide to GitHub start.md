git init
git add .
git commit -m "Initial commit"
git branch -M Main
git remote add origin https://github.com/sock-puppet-dev/HTMLACSS.git
git push -u origin Main

git switch Main
git branch -M main
git push -u origin main
git push origin --delete Main