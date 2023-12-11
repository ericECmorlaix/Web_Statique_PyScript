---
template: pyscript.html
---
# Introduction à PyScript

## Kesako

PyScript est une boite à outils (un framework) qui permet aux développeurs d'ajouter une logique Python _"pour donner vie"_ à l'interface HTML (le [DOM](https://la-cascade.io/articles/le-dom-cest-quoi-exactement){target=_blank}) de leurs pages WEB et ainsi créer des applications interactives fonctionnant dans un navigateur.

![kesako PyScript](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRF__EJSdwxNWURtTHkuST0NcYnwnSYesBzc0W6lXrXKieKx3Glu9lW8zDgGYaf-i2Y8pI&usqp=CAU){.center}

<!-- (https://www.jhanley.com/wp-content/uploads/2022/05/pyscript-what-is-it.jpg) -->

PyScript est un méta-projet qui combine plusieurs technologies ouvertes comme [Pyodide](https://pyodide.org/en/stable/){target=_blank} , [MicroPython](https://micropython.org/){target=_blank} et [WASM](https://webassembly.org/){target=_blank} entre autres technologies Web modernes.

## Exemple

C'est PyScript qui me permet d'intégrer des cellules interactives de code Python directement dans cette page afin de vous proposer l'activité suivante :

<div>
    <py-repl>
    def inverse_chaine(chaine):
        """
        Compléter la docstring... 
        """
        chaine_inverse = '' # Commenter cette instruction...
        # Commenter le bloc d'instructions...
        for caractere in chaine:            
            chaine_inverse = caractere + chaine_inverse # Commenter cette instruction...
        return chaine_inverse # Commenter cette instruction...

    def est_palindrome(chaine):
        """
        Compléter la docstring... 
        """
        chaine_inverse = inverse_chaine(chaine) # Commenter cette instruction...
        # Commenter le bloc d'instructions...
        if chaine.lower() == "kayak" :
            print("'kayak' est un faux ami, à l'envers il fait 'glouglou' !") # Commenter cette instruction...
        else :
            return chaine == chaine_inverse # Commenter cette instruction...

    print("Maintenant que ces fonctions sont définie, on peut les tester...")
    </py-repl>
    <py-repl>
        # test 1 : doit renvoyer 'NSI'
    inverse_chaine('ISN')
    </py-repl>
    <py-repl>
        # test 2 : doit renyoyer False
    est_palindrome('NSI')
    </py-repl>
    <py-repl>
        # tests 3 : doit renyoyer True
    est_palindrome('ISN-NSI')
    </py-repl>
    <py-repl>
        # tests 4 : ???
    est_palindrome('kayak')
    </py-repl>
    <py-repl id="my-repl" auto-generate=true>
        # Réaliser vos propres tests :
    ...
    </py-repl>
    </div>

???+ example "A faire vous même n°1 : ..."
    
    - **Exécuter** successivement les instructions des cellules [REPL](https://en.wikipedia.org/wiki/Read-eval-print_loop){target=_blank} ci-dessus avec la combinaison de touches ++"⇑ Maj."+"Entrée ↵"++ ;
    - **Compléter** la docstring et les commentaires des fonctions `inverse_chaine(chaine)` et `est_palindrome(chaine)` en précisant le typage des entrée/sortie ;
    - **Copier/Coller** les codes ainsi complétés dans le [notebook de retour d'activité sur Capytale](https://capytale2.ac-paris.fr/web/c/d76b-2521137){target=_blank} ;

## Principe de PyScript

### Dans le <head>

Il faut inclure dans le `<head>` deux balises :
```html
<head>
  <!-- Pour appliquer le CSS de PyScript -->  
  <link rel="stylesheet" href="https://pyscript.net/releases/2023.12.1/core.css">
  <!-- Pour amorcer PyScript -->
  <script type="module" src="https://pyscript.net/releases/2023.12.1/core.js"></script>  
</head>
```

### Dans le <body>

Il faut inclure dans le `<body>` des balises `<script>` :
```html
<h1>Une page avec PyScript</h1>
<p>
    <strong>
        <script type="py">
            from pyscript import display
            for _ in range(10) :
                display("Bonjour le web") # s'affiche dans le DOM
        </script>
    </strong>
</p>
<img src="https://pyscript.github.io/docs/2023.12.1/assets/images/pyscript.svg" width=60%>
<script type="py" terminal>
    print("Bonjour le terminal") # s'affiche dans le terminal
</script>
```
Avec :
- Le `type="py"` pour l'interpréteur Pyodide ou `type="mpy"` pour MicroPython ;
- Le mot clé `terminal` ajoute un terminal pour afficher les `print()` ;
- Le mot clé `worker` permet les `input()` dans le terminal ;

???+ example "A faire vous même n°2 : ..."
    
    - **Cliquer** sur le bouton vert `Use this template` pour **créer** un nouveau dépôt GitHub à partir du [Templtate_Web_Statique_PyScript](https://en.wikipedia.org/wiki/Read-eval-print_loop){target=_blank} ;
    - **Observer** les résultat sur votre site ;
    - **Personaliser** le code de la page ;
    - **Copier/Coller** l'URL de votre site dans le [notebook de retour d'activité sur Capytale](https://capytale2.ac-paris.fr/web/c/d76b-2521137){target=_blank} ;

## Autre exemple

**Ajouter** une nouvelle `page.html` pour votre chiffrement de César en vous inspirant de la [documentation beginning-pyscript](https://pyscript.github.io/docs/2023.12.1/beginning-pyscript/){target=_blank} ;


## Ressources

- [Documentation PyScript version 2023.12.1](https://pyscript.github.io/docs/2023.12.1/){target=_blank} ;

<!-- 


### `<script type="py-editor">`

Si vous spécifiez le type `py-editor`(pour Pyodide) ou `mpy-editor`(pour MicroPython) dans une balise `<script>`, le plugin crée un éditeur de code visuel en mode REPL genre notebook jupyter, avec un bouton pour exécuter le code contenu dans la cellule; L'utilisateur peut alors modifier le code et aussi ajouter des cellules.

=== "Le code :"
    ```html
    <script type="py-editor">
    import sys
    print(sys.version)
    </script>
    <script type="mpy-editor">
    import sys
    print(sys.version)
    a = 42
    print(a)
    </script>    
    ```
=== "Produit :"
    <script type="py-editor">
    import sys
    print(sys.version)
    </script>
    <script type="mpy-editor">
    import sys
    print(sys.version)
    a = 42
    print(a)
    </script>




###  `<py-script>`

=== "Le code :"
    ```html
    <py-script>
    display("Demat d'an holl !")
    </py-script>
    ```
=== "Produit :"
    <py-script>
    display("Demat d'an holl !")
    </py-script>

***

=== "Le code :"
    ```html
    <py-script src="./pyscripts/toto.py"></py-script>
    ```
=== "Produit :"
    <py-script src="./pyscripts/toto.py"></py-script>
=== "Avec dans le fichier `toto.py` :"
    ```python
    display('Toto est dans la place !')
    ```
***

=== "Le code :"
    ```html
    <p><strong>Aujourd'hui nous sommes le <label id='date'></label></strong></p>
    <py-script>
    import time
    pyscript.write('date', time.strftime('%d/%m/%Y %H:%M:%S'))
    </py-script>
    ```
=== "Produit :"
    <p><strong>Aujourd'hui nous sommes le <label id='date'></label></strong></p>
    <py-script>
    import time
    pyscript.write('date', time.strftime('%d/%m/%Y %H:%M:%S'))
    </py-script>
***



***

=== "Le code :"
    ```html
    <div>
    <py-repl>
    def inverse_chaine(chaine):
        chaine_inverse = ''
        for caractere in chaine:
            chaine_inverse = caractere + chaine_inverse
        return chaine_inverse
    def est_palindrome(chaine):
        chaine_inverse = inverse_chaine(chaine)
        if chaine.lower() == "kayak" :
            print("'kayak' est un faux ami, à l'envers il fait 'glouglou' !")
        else :
            return chaine == chaine_inverse
    </py-repl>
    <py-repl>
        # test 1 : doit renvoyer 'NSI'
    inverse_chaine('ISN')
    </py-repl>
    <py-repl>
        # test 2 : doit renyoyer False
    est_palindrome('NSI')
    </py-repl>
    <py-repl>
        # tests 3 : doit renyoyer True
    est_palindrome('ISN-NSI')
    </py-repl>
    <py-repl>
        # tests 4 : ???
    est_palindrome('kayak')
    </py-repl>
    <py-repl id="my-repl" auto-generate=true>
        # Réaliser vos propres tests :
    ...
    </py-repl>
    </div>
    ```
=== "Produit :"
    <div>
    <py-repl>
    def inverse_chaine(chaine):
        chaine_inverse = ''
        for caractere in chaine:
            chaine_inverse = caractere + chaine_inverse
        return chaine_inverse
    def est_palindrome(chaine):
        chaine_inverse = inverse_chaine(chaine)
        if chaine.lower() == "kayak" :
            print("'kayak' est un faux ami, à l'envers il fait 'glouglou' !")
        else :
            return chaine == chaine_inverse
    </py-repl>
    <py-repl>
        # test 1 : doit renvoyer 'NSI'
    inverse_chaine('ISN')
    </py-repl>
    <py-repl>
        # test 2 : doit renyoyer False
    est_palindrome('NSI')
    </py-repl>
    <py-repl>
        # tests 3 : doit renyoyer True
    est_palindrome('ISN-NSI')
    </py-repl>
    <py-repl>
        # tests 4 : ???
    est_palindrome('kayak')
    </py-repl>
    <py-repl id="my-repl" auto-generate=true>
        # Réaliser vos propres tests :
    ...
    </py-repl>
    </div>



***

=== "Le code :"
    ```html
    <py-repl>
    def indice_min(nombres : list) -> int :
        indice = 0
        minimum = nombres[0]
        for i in range(len(nombres)) :
            if minimum > nombres[i] :
                minimum = nombres[i]
                indice = i
            return indice
    </py-repl>
    <py-repl>
        # test 1 : doit renvoyer 2
    indice_min([2, 4, 1, 1])
    </py-repl>
    <py-repl>
        # test 2 : doit renyoyer True
    indice_min([5]) == 0
    </py-repl>
    <py-repl>
        # tests 3 : ne doit pas renvoyer de message d'erreur
    assert indice_min([2, 4, 1, 1]) == 2
    </py-repl>
    <py-repl id="my-repl" auto-generate=true>
        # Réaliser vos propres tests :
    indice_min(...)
    </py-repl>
    ```
=== "Ne produit plus de bug"
    <py-repl>
    def indice_min(nombres : list) -> int :
        indice = 0
        minimum = nombres[0]
        for i in range(len(nombres)) :
            if minimum > nombres[i] :
                minimum = nombres[i]
                indice = i
            return indice
    </py-repl>
    <py-repl>
        # test 1 : doit renvoyer 2
    indice_min([2, 4, 1, 1])
    </py-repl>
    <py-repl>
        # test 2 : doit renyoyer True
    indice_min([5]) == 0
    </py-repl>
    <py-repl>
        # tests 3 : ne doit pas renvoyer de message d'erreur
    assert indice_min([2, 4, 1, 1]) == 2
    </py-repl>
    <py-repl id="my-repl" auto-generate=true>
        # Réaliser vos propres tests :
    indice_min(...)
    </py-repl>        
=== "Bug maintenant résolu :"

    [fix: < and > are parsed with HTML escape symbols](https://github.com/pyscript/pyscript/pull/481){target=_blank)}
    


***

### `<py-env>`

=== "Le code :"
    ```html
    <py-env>
    - paths:
      - ./pyscripts/mes_fonctions.py
    </py-env>
    <py-script>  
    from mes_fonctions import calcul_pi
    print("Calculons π :")      
    pi = calcul_pi(100000)
    s = f"π vaut approximativement {pi:.4f}"
    print(s)
    </py-script>
    ```
=== "Produit :"
    <py-env>
    - paths:
      - ./pyscripts/mes_fonctions.py
    </py-env>
    <py-script>  
    from mes_fonctions import calcul_pi
    display("Calculons π :")      
    pi = calcul_pi(100000)
    s = f"π vaut approximativement {pi:.4f}"
    display(s)
    </py-script>
=== "Avec dans le fichier `mes_fonctions.py` :"
    ```python
    def calcul_pi(n):
        pi = 2
        for i in range(1,n):
            pi *= 4 * i ** 2 / (4 * i ** 2 - 1)
        return pi
    ```


### `<py-title>`

=== "Le code :"
    ```html
    <py-title>Un titre centré</py-title>
    ```
=== "Produit :"
    <py-title>Un titre centré</py-title>


<py-title>Inventaire à finaliser...</py-title>

### `<py-inputbox>`

  <!-- <py-inputbox>
def on_keypress(event):
    print(event)
  </py-inputbox>

### `<py-box>`



### `<py-button>`

   <py-button label="Click me" styles="btn big">
def on_click(event):
    print(event)
  </py-button>



### `<py-config>`

 -->
