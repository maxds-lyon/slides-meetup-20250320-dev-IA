---
theme: ./theme
addons: 
  - slidev-addon-rabbit
rabbit:
  slideNum: true

title: < titre >
titleTemplate: '%s - 2024'
logoHeader: 'images/logo.svg'
website: 'maxds.fr'
handle: 'maxds'

drawings:
  persist: false
mdc: false

layout: center
transition: slide-left

hideInToc : true
---
# < titre >

## < sous-titre >

<!-- Introduction -->
---
src: ./pages/_introduction.md
---

<!-- TOC -->
---
src: ./pages/_toc.md
---

<!-- contents -->
---
src: ./pages/part_00.md
---

---
src: ./pages/part_01.md
---

---
src: ./pages/part_02.md
---

---
src: ./pages/part_03.md
---

---
src: ./pages/part_04.md
---

<!-- Conclusion -->
---
src: ./pages/_conclusion.md
---