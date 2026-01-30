# 🔁 Daily Routine: How to Start Working

Every time you want to work on the course:

**🍎 macOS & 🐧 Linux:**
```bash
cd ~/Documents/courses/prompt-eng
conda activate prompt-eng
jupyter lab
```

**🪟 Windows:**
```powershell
cd "$env:USERPROFILE\Documents\courses\prompt-eng"
conda activate prompt-eng
jupyter lab
```

**Note:** If you see "Module not found" errors, you likely forgot to run `conda activate prompt-eng`!

---

## When Finished

- Close browser tab
- In terminal, press `Ctrl + C` twice to stop JupyterLab
- Type `conda deactivate` to exit the environment
- Type `exit` to close terminal
