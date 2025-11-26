
git checkout main
echo "Linea original" > conflicto.txt
git add conflicto.txt
git commit -m "Archivo base para generar conflicto"
git checkout -b ramaA
echo "Cambio desde rama A" > conflicto.txt
git add conflicto.txt
git commit -m "Cambio en conflicto.txt desde rama A"
git checkout main
git checkout -b ramaB
echo "Cambio diferente desde rama B" > conflicto.txt
git add conflicto.txt
git commit -m "Cambio en conflicto.txt desde rama B"
git checkout main
git merge ramaA -m "Merge de ramaA a main"
git merge ramaB

