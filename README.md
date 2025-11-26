
git checkout -b main 2>/dev/null || git checkout main
echo "Linea original para conflicto" > conflicto.txt
git add conflicto.txt
git commit -m "Commit inicial con archivo para conflicto"
git checkout -b ramaA
echo "Cambio desde rama A" > conflicto.txt
git add conflicto.txt
git commit -m "Modificación en conflicto.txt desde rama A"
git checkout main
git checkout -b ramaB
echo "Cambio diferente desde rama B" > conflicto.txt
git add conflicto.txt
git commit -m "Modificación en conflicto.txt desde rama B"
git checkout main
git merge ramaA -m "Merge de ramaA a main"
git merge ramaB
git add conflicto.txt
git commit -m "Conflicto resuelto"
git log --graph --decorate --oneline --all
