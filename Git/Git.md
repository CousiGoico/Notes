# Create project Angular+Material

    ng new {ProjectName}; 
    cd {ProjectName}; 
    npm install @angular/material; 
    git init; 
    git add .; 
    git commit -m "initial commit"; 
    git remote add {ProjectName}Remote https://cloudArchitectSogeti@dev.azure.com/cloudArchitectSogeti/Sogeti%20Technical%20Community/_git/AngularElectron; 
    git remote -v;
    git push --set-upstream {ProjectName}Remote main;

# Create a new branch

[//]: <> (Option 1)
    git branch $newBranchName;
    git checkout $newBranchName;

[//]: <> (Option 2)
    git checkout -b $newBranchName;

    git push --set-upstream origin $newBranchName;
    git push;


# Add remote

    git add remote {name} {url_repo}

    git remote -v // check exists the remote

    git push --set-upstream {name} main

# Git tag

## Create

    git tag -a {tagName} -m "{message}"; git push origin {tagName}

    git tag -a v1.3 -m "My version v1.3"; git push origin v1.3

## Delete

    git tag -d {tagName}; git push origin --delete {tagName}

    git tag -d v1.3; git push origin --delete v1.3

# Git Stash

## List

Lista los cambios pendientes de commitear

    git stash list

## Show

Muestra los cambios pendientes de commitear

    git stash show

## Pop

Remueve un stash del listado

    git stash pop [--index]

## Push

Añade los ficheros modificados a un stash. Equivalente a git stash sin aargumentos.

    git stash

## Clear

Elimina todos los stash

    git stash clear