# Manual: Configurar GitHub para Obsidian - Proyecto Brigadeiros Alegria
**Autor:** Jimmy Gallo Morales (Jimco62)  
**Fecha:** Octubre 2026  
**Vault:** `C:\Users\jimco\Documents\brigadeiros-alegria`  
**Repo:** `Jimco62/brigadeiros-alegria`

## Objetivo
Tener respaldo automático, historial de versiones y sincronización en la nube para tu vault de Obsidian usando Git + GitHub + Plugin Obsidian Git.

---

## 1. Software Necesario
- `Git-2.50.0-64-bit.exe` -> Motor de versionado
- `GitHubDesktopSetup-x64.exe` -> Interfaz visual
- `VSCodeUserSetup-x64-1.144.0.exe` -> Editor por defecto de Git
- Node.js (`node-v26.13.0-x64.msi`) -> **ACLARACIÓN:**
  - **Fase 1 (Backup Obsidian + GitHub):** NO necesario. Con Git + GitHub Desktop + Obsidian Git basta. Es tu sistema interno privado.
  - **Fase 2 (Web Lectura - npx quartz sync):** SÍ necesario, OBLIGATORIO. Sin Node no funciona `npx quartz sync` para ver el vault en navegador desde cualquier equipo.

### Instalación de Git
1. Ejecutar `Git-2.50.0-64-bit.exe`
2. En "Choosing the default editor" elegir **Use Visual Studio Code as Git's default editor**
3. Dejar todo lo demás por defecto
4. Verificar en CMD:
```bash
git --version
git config --global user.name "Jimmy Gallo Morales"
git config --global user.email "tu-email@github.com"
```

### Instalación de GitHub Desktop
1. Ejecutar `GitHubDesktopSetup-x64.exe`
2. Loguearse con cuenta de GitHub
3. Configurar nombre y email

---

## 2. Preparar el Vault en GitHub

### El problema del nombre
Tu carpeta local era `Brigadeiros Alegria` (con espacio) y GitHub no permite espacios. Se unifica a `brigadeiros-alegria` con guión y minúsculas.

### Pasos
1. En GitHub.com crear repo `brigadeiros-alegria` (Private)
2. En GitHub Desktop: `Clone Jimco62/brigadeiros-alegria` en `C:\Users\jimco\Documents\`
3. Se crea `C:\Users\jimco\Documents\brigadeiros-alegria` vacía y conectada
4. Copiar TODO el contenido de la carpeta vieja `Brigadeiros Alegria` a la nueva `brigadeiros-alegria`

---

## 3. Crear .gitignore

Para no subir archivos basura que cambian cada segundo, crear archivo `.gitignore` en la raíz del vault:

```
.obsidian/workspace.json
.obsidian/workspace-mobile.json
.obsidian/hotkeys.json
.obsidian/appearance.json
.trash/
```

> En tu caso desmarcaste `workspace.json` manualmente antes del primer commit.

---

## 4. Primer Commit y Push

En GitHub Desktop viste esto después de pegar tus archivos:

> 13 changed files - Listado de tus notas de Panel, Marca, Producto, Finanzas, etc.

1. Desmarcar `workspace.json`
2. Escribir en Summary: `backup inicial - panel, propuesta, identidad y costos`
3. `Commit to main`
4. `Push origin`

Resultado: `No local changes`

[Push exitoso](01-push-exitoso.png)

---

## 5. Configurar Plugin Obsidian Git

1. En Obsidian: Settings -> Community Plugins -> Browse -> Buscar solo `Git`
2. Instalar `Git Por Vinzent` (el de 3.3M descargas, el más popular)
3. Enable

### Error "Git is not ready" - Solución
Ir a Settings -> Git -> `Custom Git binary path` (debajo de Advanced) y poner:

```
C:\Program Files\Git\cmd\git.exe
```
Alternativa:
```
C:\Program Files\Git\bin\git.exe
```
Reiniciar Obsidian.

### Configuración Automática
En Settings -> Git:

**Automatic:**
- Auto commit-and-sync interval: `10`
- Auto commit-and-sync after stopping file edits: `ON`

**Sync:**
- Pull changes on startup: `ON`
- Push on backup: `ON`

---

## 6. Flujo Diario dentro de Obsidian

1. Abrir paleta `Ctrl + P` -> `Git: Open source control view`
2. Verás 3 botones clave:
   - `+` con flecha = Stage all (pasar a Staged Changes)
   - `✓` = Commit
   - `↑` = Push (cuando está morado, hay cambios por subir)

Cuando instalaste el plugin aparecieron 5 archivos nuevos del plugin:
`community-plugins.json, data.json, main.js, manifest.json, styles.css`

Flujo para guardarlos:
- Stage: clic en `+ 5` en Changes -> pasa a `Staged Changes - 5`
- Commit: clic en `✓`
- Push: clic en `↑` morado

Mensaje final: `Pushed 5 files to remote`

[Repo en GitHub](02-repo-en-github.png)

---

## 7. Verificación Final en GitHub

Ir a `github.com/Jimco62/brigadeiros-alegria` -> Verás:

- .obsidian/
- 00 - Panel Principal
- 01 - Marca e Identidad
- 02 - Producto y Recetas
- 03 - Finanzas y Costos
- 04 - Web y Ventas
- 05 - Marketing y Redes
- 99 - Templates
- .gitignore
- LICENSE
- README.md

¡Todo respaldado!

---

## 8. Mantenimiento

- Borrar carpeta vieja `Brigadeiros Alegria` con espacio
- Siempre abrir en Obsidian la nueva `brigadeiros-alegria`
- Ya no necesitas abrir GitHub Desktop, Obsidian hace todo solo
- Para recuperar una versión vieja: `Ctrl + P` -> `Git: Open history view`

---

## Comandos Útiles (Opcional - Terminal)

```bash
git status
git log --oneline
git commit -m "nueva receta brigadeiro pistacho"
git push
```

---

Generado automáticamente después de la configuración exitosa del 31 Oct 2026.


