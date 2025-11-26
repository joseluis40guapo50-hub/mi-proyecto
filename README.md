# 1. Asegurarte de estar en main
git checkout main

# 2. Crear un archivo base que luego causará conflicto
echo "Linea original" > conflicto.txt
git add conflicto.txt
git commit -m "Archivo base para generar conflicto"

# 3. Crear rama A (development por ejemplo)
git checkout -b ramaA
echo "Cambio desde rama A" > conflicto.txt
git add conflicto.txt
git commit -m "Cambio en conflicto.txt desde rama A"

# 4. Volver a main
git checkout main

# 5. Crear rama B que producirá el conflicto
git checkout -b ramaB
echo "Cambio diferente desde rama B" > conflicto.txt
git add conflicto.txt
git commit -m "Cambio en conflicto.txt desde rama B"

# 6. Volver a main y fusionar ramaA
git checkout main
git merge ramaA -m "Merge de ramaA a main"

# 7. Ahora intentar fusionar ramaB (esto generará el conflicto)
git merge ramaB

