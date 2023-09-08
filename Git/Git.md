
ng new {ProjectName}; 
cd {ProjectName}; 
npm install @angular/material; 
git init; 
git add .; 
git commit -m "initial commit"; 
git remote add {ProjectName}Remote https://cloudArchitectSogeti@dev.azure.com/cloudArchitectSogeti/Sogeti%20Technical%20Community/_git/AngularElectron; 
git remote -v;
git push --set-upstream {ProjectName}Remote main;