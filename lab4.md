# LAB5 : Git - Fusion et Rebase

## Objectifs :
- Créer des branches et naviguer entre elles.
- Fusionner des branches avec `git merge`.
- Utiliser `git merge --squash` pour unifier plusieurs commits.
- Comprendre et appliquer `git rebase`.

---

## A. Création et Gestion des Branches

1. **Créer une branche `hotfix` et s'y positionner**
   ```sh
   git branch hotfix
   git checkout hotfix
   ```
  

2. **Créer et committer deux fichiers sur `hotfix`**
   ```sh
   echo "Correction 1" > HotfixFile1.txt
   git add HotfixFile1.txt
   git commit -m "Ajout de HotfixFile1.txt"

   echo "Correction 2" > HotfixFile2.txt
   git add HotfixFile2.txt
   git commit -m "Ajout de HotfixFile2.txt"
   ```

3. **Revenir à `master` et vérifier la position du HEAD**
   ```sh
   git checkout master
   git log --oneline --graph --all
   ```

4. **Créer et committer deux fichiers sur `master`**
   ```sh
   echo "Fichier principal 1" > MasterFile1.txt
   git add MasterFile1.txt
   git commit -m "Ajout de MasterFile1.txt"

   echo "Fichier principal 2" > MasterFile2.txt
   git add MasterFile2.txt
   git commit -m "Ajout de MasterFile2.txt"
   ```

---

## B. Fusionner une Branche avec `git merge`

5. **Fusionner `hotfix` dans `master`**
   ```sh
   git merge hotfix
   ```

6. **Vérifier que les fichiers de `hotfix` sont bien présents dans `master`**
   ```sh
   ls
   ```

7. **Visualiser l'historique des commits**
   ```sh
   git log --oneline 
   ```

---

## C. Utilisation de `git merge --squash`

8. **Créer une branche `squashBranch` et y ajouter un fichier**
   ```sh
   git branch squashBranch
   git checkout squashBranch
   echo "Squash test 1" > squashtest1.txt
   git add squashtest1.txt
   git commit -m "Ajout de squashtest1.txt"
   ```

9. **Revenir à `master` et ajouter un fichier**
   ```sh
   git checkout master
   echo "Main squash test" > MainSquashtest1.txt
   git add MainSquashtest1.txt
   git commit -m "Ajout de MainSquashtest1.txt"
   ```

10. **Ajouter un autre fichier sur `squashBranch`**
   ```sh
   git checkout squashBranch
   echo "Squash test 2" > squashtest2.txt
   git add squashtest2.txt
   git commit -m "Ajout de squashtest2.txt"
   ```

11. **Revenir à `master` et fusionner avec `--squash`**
   ```sh
   git checkout master
   git merge --squash squashBranch
   ```

12. **Faire un commit unique après le squash**
   ```sh
   git commit -m "Merge squash into master"
   ```

13. **Vérifier l’historique après le squash**
   ```sh
   git log --oneline --graph --decorate
   ```

---

## D. Utilisation de `git rebase`

14. **Créer une branche `rebaseBranch` et y ajouter des fichiers**
   ```sh
   git branch rebaseBranch
   git checkout rebaseBranch
   echo "Rebase fichier 1" > rebase1.txt
   git add rebase1.txt
   git commit -m "Ajout de rebase1.txt"

   echo "Rebase fichier 2" > rebase2.txt
   git add rebase2.txt
   git commit -m "Ajout de rebase2.txt"
   ```

15. **Revenir à `master` et appliquer `rebase`**
   ```sh
   git checkout master
   git rebase rebaseBranch
   ```

16. **Vérifier l’arborescence des commits**
   ```sh
   git log --oneline 
   ```

---

## Conclusion
- `git merge` fusionne les branches et conserve l'historique.
- `git merge --squash` combine plusieurs commits en un seul avant la fusion.
- `git rebase` permet d'appliquer les commits d'une branche sur une autre en réécrivant l'historique.

📌 *Pour plus d’informations, consultez la [documentation Git](https://git-scm.com/doc).*
