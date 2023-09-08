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