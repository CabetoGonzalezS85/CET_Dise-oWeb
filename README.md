# 🚀 Guía Completa de Git + GitHub con SSH

Este documento es una guía de referencia rápida y práctica para trabajar con **Git** y **GitHub**, desde la inicialización de un repositorio hasta el manejo de ramas, usando autenticación por **SSH**.

---

## 🛠️  1. Inicializar el Repositorio Local

```bash
git init
```

---

## 📁 2. Agregar Archivos y Hacer Commit

```bash
git add .
git commit -m "Primer commit: subiendo proyecto"
```

---

## 🔐 3. Configurar SSH para GitHub

### 3.1 Verificar si ya tienes una clave SSH:

```powershell
dir $env:USERPROFILE\.ssh
```

### 3.2 Generar nueva clave SSH (sin passphrase):

```bash
ssh-keygen -t ed25519 -C "tu-email@ejemplo.com"
```
Presiona Enter en todas las preguntas para aceptar los valores por defecto.

### 3.3 Copiar la clave pública:

```powershell
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub
```

Pega el contenido en GitHub:  
**GitHub > Settings > SSH and GPG Keys > New SSH Key**

### 3.4 Probar conexión:

```bash
ssh -T git@github.com
```

---

## 🔗 4. Conectar tu Proyecto Local con GitHub (SSH)

### Si es la primera vez:

```bash
git remote add origin git@github.com:TuUsuario/TuRepositorio.git
```

### Si ya existe y quieres corregirlo:

```bash
git remote set-url origin git@github.com:TuUsuario/TuRepositorio.git
```

### Verificar conexión remota:

```bash
git remote -v
```

---

## 🚀 5. Subir Proyecto a GitHub

```bash
git push -u origin main
```

### Si hay conflicto con el repositorio remoto:

```bash
git pull --rebase origin main
git push -u origin main
```

### O forzar el push (con precaución):

```bash
git push -u origin main --force
```

---

## 🌱 6. Trabajar con Ramas

### Crear nueva rama y moverse a ella:

```bash
git checkout -b nombre-de-la-rama
```

### Ver ramas locales:

```bash
git branch
```

### Cambiar a otra rama:

```bash
git checkout nombre-de-la-rama
```

### Subir rama al repositorio remoto:

```bash
git push -u origin nombre-de-la-rama
```

---

## 🔁 7. Fusionar Ramas (Merge)

```bash
git checkout main
git pull origin main
git merge nombre-de-la-rama
git push origin main
```

---

## 🧽 8. Eliminar Ramas

### Eliminar rama local:

```bash
git branch -d nombre-de-la-rama
```

### Forzar eliminación local:

```bash
git branch -D nombre-de-la-rama
```

### Eliminar rama remota:

```bash
git push origin --delete nombre-de-la-rama
```

---

## 📅 9. Descargar Últimos Cambios (Pull)

```bash
git pull origin main
```

---

## 🪥 10. Archivos a Ignorar (.gitignore)

Ejemplo de contenido:

```
# Configuración del editor
.vscode/
.idea/

# Archivos temporales
*.log
*.tmp
.DS_Store

# Dependencias
node_modules/
```

---

## 🧠 11. Comandos ÚTiles

### Ver estado de archivos:

```bash
git status
```

### Ver historial de commits:

```bash
git log --oneline --graph --all
```

### Guardar cambios sin hacer commit:

```bash
git stash
```

---

## ✅ 12. Flujo de Trabajo Sugerido

```bash
git init
git add .
git commit -m "Primer commit"
git remote add origin git@github.com:TuUsuario/TuRepositorio.git
git push -u origin main

# Crear y trabajar en una rama

git checkout -b feature/nueva-funcionalidad
git add .
git commit -m "Nueva funcionalidad"
git push -u origin feature/nueva-funcionalidad

# Fusionar en main

git checkout main
git pull origin main
git merge feature/nueva-funcionalidad
git push origin main
```

---

## 📊 Buenas Prácticas

- Usa nombres de ramas descriptivos: `feature/`, `fix/`, `hotfix/`
- Haz commits pequeños, claros y frecuentes
- Nunca subas archivos confidenciales (claves, tokens, etc.)
- Usa un `.gitignore` bien configurado
- Siempre haz `pull` antes de `push`
- Documenta tu proyecto con `README.md`

---

## 🙏 Agradecimientos

Guía creada por **CabetoGonzalezS85** junto a **DevMaster AI** 🧠
github.com/CabetoGonzalezS85

---

