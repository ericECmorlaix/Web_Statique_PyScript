
```html

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Web avec PyScript</title>

    <!-- Pour appliquer le CSS de PyScript -->  
    <link rel="stylesheet" href="https://pyscript.net/releases/2023.12.1/core.css">
    <!-- Pour amorcer PyScript -->
    <script type="module" src="https://pyscript.net/releases/2023.12.1/core.js"></script>
    

</head>
<body>
    <h1>Une autre page avec PyScript</h1>

    <div>
        <input type="text" name="entree" id="entree" placeholder="Saisir le mot de passe ici..." />
        <button py-click="ma_fonction">Valider</button>
        <div id="sortie"></div>
        <script type="py" src="./programme.py" ></script>
    
    </div>   
</body>
```
```python
# Le mot de passe du village
from pyscript import document

def ma_fonction(event):
    entree_text = document.querySelector("#entree")
    sortie_div = document.querySelector("#sortie")
    if entree_text.value() == "64741" :
        sortie_div.innerText = "Bon festin..."
    else:
        sortie_div.innerText = "Allez-vous en !"
```
