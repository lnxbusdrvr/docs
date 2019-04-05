## Miten kerrotan Gitille, että haluat pushata olemassa olevaan repoon

(https://kbroman.org/github_tutorial/pages/init.html) 

Monesti nämä ekat komennot saattaa olla turhia: <br>
```
git clone <repo-url.git>
git init
```

**Tärkeimmät komennot: ** <br>
```
git add .
git commit -m "Some informative text here. No cursewordas, or/and other lamewords  to make it more PRO"
git remote add origin git@github.com:username/exiting_repo.git
git push -u origin someBranch
```
