---
marp: true
theme: default
paginate: true
footer: ![height:20px](img/twitter.svg) ![height:20px](img/github.svg) @jtpio @QuantStack
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
  }
---

<style>
section::after {
  content: attr(data-marpit-pagination) '/' attr(data-marpit-pagination-total);
}
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
</style>

![bg fit right:30%](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/icon.svg)

# Interactive computing in the browser with Jupyterlite

## JOBIM 2024

### Jérémy Tuloup

https://jtp.io/jobim-2024

---

# Jérémy Tuloup

- Technical Director à QuantStack
- Jupyter Distinguished Contributor
- Jupyter Frontends SSC (Steering Software Council) representative
- Contributor and maintainer of many Jupyter projects
- JupyterLite creator

---

# Quick History

![bg fit right:30%](https://jupyter.org/assets/homepage/main-logo.svg)

---

# IPython in the terminal

![fit](https://ipython.readthedocs.io/en/stable/_images/ipython-6-screenshot.png)

---

# REPL: Read Eval Print Loop

---

# Why are notebooks popular ?

- REPL workflow
- with:
  - **narration**
  - **memory**
  - **reproducibility**
  - **communication**

---

# IPython Notebook

![fit](https://user-images.githubusercontent.com/591645/228060329-13368066-b1e9-4812-9662-70919d833a77.png)

---

# Jupyter Notebook

![fit 90%](img/jupyter-notebook.png)

---

# JupyterLab

![fit 90%](img/jupyterlab.png)

---

# LIGO

<div class="columns">


<div>
<img src="https://github.com/jtpio/alposs-2024/assets/591645/ebcf3de3-7e5e-43ec-87a4-c7cc19379680" />
</div>

<div>
<img src="https://github.com/jtpio/alposs-2024/assets/591645/2aa58b86-b9d8-437d-8153-345f00a73b08" />
</div>

</div>

---

# Black Hole M87

<div class="columns">

<div>
<img src="https://github.com/jtpio/alposs-2024/assets/591645/3600c6d4-1894-48f1-9855-4d760d53e84c">
</div>

<div>
<img src="https://github.com/jtpio/alposs-2024/assets/591645/c1cb7afe-0840-48b7-9708-67b5bd7fd0ff">

</div>

</div>

---

# The Jupyter ecosystem

- Navigating the Jupyter Landscape
  - JupyterCon 2023 (Paris)
  - Jeremy Tuloup, Johan Mabille
  - https://www.youtube.com/watch?v=uWJ0-OPKTxI

---

![bg fit 60%](img/repos_map.svg)

---

![bg fit](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/icon.svg)

---

# JupyterLite

- Everything runs in the browser via WebAssembly
- Based on the Jupyter stack:
  - Pyodide and Xeus kernels run code in the browser
  - JupyterLab and Jupyter Notebook interfaces
  - Voici for web applications and dashboards

---

# Jupyter

![center](https://user-images.githubusercontent.com/591645/228267004-e4e2e54f-1d5f-45b7-bacb-6c3a1844c479.png)

---

# JupyterLite

![center](https://user-images.githubusercontent.com/591645/237059523-d29b94e6-7287-4608-b617-b0fe2a74877a.png)

---


![bg fit 60%](./img/jupyterlite.png)

---

# Wasm powered Jupyter running in the browser

- https://developer.mozilla.org/en-US/docs/WebAssembly

![center h:400px](https://user-images.githubusercontent.com/591645/162831191-16956085-783a-435e-b810-0d25da1379b3.png)

---

# Python in the browser

![center h:200px](https://github.com/jtpio/jobim-2024/assets/591645/771dc6ca-8ae3-418a-8368-f036df0ffbd6)

- Pyodide
- CPython compiled to WebAssembly
- Xeus Python + Emscripten Forge

---

![bg fit 75%](./img/jupyterlite.svg)

---

# Jupyter and Python in the browser

![center w:512](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/badge-launch.svg)

- ✅ no Python server
- ✅ no command line for users
- ✅ no need to install Python and other packages locally
- ✅ can be hosted as a static site

---

# A Jupyter web site available in a few seconds

![center h:600px](https://user-images.githubusercontent.com/591645/120649478-18258400-c47d-11eb-80e5-185e52ff2702.gif)

---

# `jupyterlite-core`: a static site generator

```shell
pip install jupyterlite-core

jupyter lite build
```

---

# HTML, CSS, JavaScript, Wasm files

<div class="columns">
<div>


```
├── api
│   └── translations
│       ├── all.json
│       └── en.json
├── bootstrap.js
├── build
│   ├── 9507.1e6cc5d.js
│   ├── 9602.62bf0f1.js
│   ├── 9621.e2e8b5d.js
│   ├── ...
│   ├── repl
│   │   ├── bundle.js
│   ├── retro
│   │   ├── bundle.js
│   ├── schemas
│   │   ├── all.json
│   │   ├── @jupyterlab
│   │   │   ├── application-extension
│   │   │   │   ├── commands.json
│   │   │   │   ├── context-menu.json
│   │   │   │   ├── shell.json
│   │   │   │   └── sidebar.json
│   ├── themes
│   │   └── @jupyterlab
│   │       ├── theme-dark-extension
│   │       │   ├── index.css
│   │       │   └── index.js
...
```
</div>
<div>

```
...
│   │       └── theme-light-extension
│   │           ├── index.css
│   │           └── index.js
├── config-utils.js
├── extensions
│       └── xeus-python-kernel
│           └── static
│               ├── numpy-1.24.2-py310h6d2fff6_0.0.data
│               ├── numpy-1.24.2-py310h6d2fff6_0.0.js
│               ├── python-3.10.2-h_hash_26_cpython.0.data
│               ├── python-3.10.2-h_hash_26_cpython.0.js
│               ├── python_data.js
│               ├── remoteEntry.35b4eac217ec6bf078a4.js
├── lab
│   ├── favicon.ico
│   ├── index.html
│   ├── jupyter-lite.ipynb
│   ├── jupyter-lite.json
│   ├── package.json
│   ├── tree
│   │   └── index.html
│   └── workspaces
│       └── index.html
...
```

</div>
</div>


---

# Easy to deploy

Served via well-cacheable, static HTTP(S) on most static web hosts

<div class="columns">
<div>

![center width:256](https://user-images.githubusercontent.com/591645/120675034-00f29080-c495-11eb-928c-26bb94e8eb68.png)
![center width:256](https://user-images.githubusercontent.com/591645/120676545-6dba5a80-c496-11eb-9b2b-604e92c3429b.png)
![center width:256](https://user-images.githubusercontent.com/591645/120675516-6f375300-c495-11eb-819c-d6f1fb3cb0f1.png)

</div>
<div>

![center width:256](https://user-images.githubusercontent.com/591645/120676313-2df37300-c496-11eb-8639-25e2fc606850.png)
![center width:256](https://user-images.githubusercontent.com/591645/236239105-d00f05df-ee79-4062-a0a8-f0f0118bbe1d.png)
![center h:128](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Amazon-S3-Logo.svg/428px-Amazon-S3-Logo.svg.png)

</div>
</div>

---

# Use cases

---

![center h:300px](https://user-images.githubusercontent.com/591645/162619390-ecab994a-3f39-4e26-af78-ca2569aee9b2.png)

```html
<iframe
  src="https://jupyterlite.github.io/demo/repl/index.html?kernel=python&toolbar=1"
  width="100%"
  height="500px"
>
</iframe>
```

---

<iframe
  src="https://jtp.io/jobim-2024/lite/repl/index.html?kernel=python&toolbar=1&code=%pip%20install%20-q%20%22ipymolstar==0.0.5%22%20%22anywidget==0.9.2%22&code=from%20ipymolstar%20import%20PDBeMolstar&code=view%20=%20PDBeMolstar(%20molecule_id=%221qyn%22,%20theme=%22light%22,%20hide_water=True,%20visual_style=%22cartoon%22,%20)"
  width="100%"
  height="500px"
>
</iframe>

---

![bg fit](https://github.com/jtpio/alposs-2024/assets/591645/c0fe58fa-c2d8-4777-a996-9a8cd8f641f7)

---

<video
  controls
  width="100%"
  height="600px"
  src="https://github.com/jtpio/alposs-2024/assets/591645/9b5e247d-cb89-4b15-aba3-97e5ab381bb5">
</video>

---

https://github.com/rowanc1/myst-lite

<video
  controls
  width="100%"
  height="600px"
  src="https://github.com/rowanc1/myst-lite/assets/913249/c62478d3-fc90-4350-8006-9a65846a2f26">

</video>

---

# 🎓 Education

- Capytale: https://capytale.fr
- Paris Saclay: https://jupyter.gitlab.dsi.universite-paris-saclay.fr/tutoriel-jupyter/utiliser.html
- UC Berkeley
- LabNBook (Université Grenoble Alpes): https://labnbook.fr/les-labdocs-code-sont-disponibles-dans-labnbook-integration-de-jupyterlite/
- Grenoble INP UGA Phelma: https://phelma-sicom.gricad-pages.univ-grenoble-alpes.fr/1a/3pmpols6-cours/TD_1.html

---

# ⌛ Reproducibility time capsule

- WebAssembly is a web standard
- Runnable for much longer than native binary packages

![center h:300](https://github.com/jtpio/jobim-2024/assets/591645/4686d0f6-8c4a-4195-8420-74a71ff0b510)

---

# :rocket: Deploy to GitHub Pages

- https://github.com/jupyterlite/demo

![center height:400px](https://raw.githubusercontent.com/jupyterlite/xeus-python-demo/main/deploy.gif)


---

https://jupyterlite.github.io/demo/


![](https://github.com/jtpio/alposs-2024/assets/591645/9e19fcea-4f17-4bd4-a83a-9eb548bd9968)

---

# :test_tube: Current developments

- In-browser terminal
- AI code completions and chat
- Real Time Collaboration via WebRTC
- Emscripten Forge and Conda Forge

---

# :sparkles: Demo :sparkles:

https://jtpio.github.io/jobim-2024/lite

---

# :sparkles: AI code completions and chat

<video
  controls
  width="100%"
  height="600px"
  src="https://github.com/jupyterlite/jupyterlab-codestral/assets/591645/855c4e3e-3a63-4868-8052-5c9909922c21">

</video>

---

# 🔍 References

- Jupyter documentation: https://docs.jupyter.org
- This presentation:
  - Repo: https://github.com/jtpio/jobim-2024
  - Slides: https://jtp.io/jobim-2024

---

# Thanks !
