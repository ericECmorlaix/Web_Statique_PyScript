---
template: pyscript.html
---

# Memo pour PyScript

![kesako PyScript](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRF__EJSdwxNWURtTHkuST0NcYnwnSYesBzc0W6lXrXKieKx3Glu9lW8zDgGYaf-i2Y8pI&usqp=CAU){.center}

<!-- (https://www.jhanley.com/wp-content/uploads/2022/05/pyscript-what-is-it.jpg) -->

## Préparation

### Page HTML

Il faut inclure dans le `<head>` deux balises :
```html
<head>
  <link rel="stylesheet" href="https://pyscript.net/latest/pyscript.css" />
  <script defer src="https://pyscript.net/latest/pyscript.js"></script>
</head>
```
### Page MkDocs MarkDown

Se référer [au résumé de configuration de Rodrigo SCHWENCKE](https://eskool.gitlab.io/mkhack3rs/pyscript/).

## Inventaire de balises

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


### `<py-repl>`

=== "Le code :"
    ```html
    <py-repl id="my-repl" auto-generate=true></py-repl>
    ```
=== "Produit :"
    <<py-repl id="my-repl" auto-generate=true></py-repl>

> Saisir une instruction Python dans la cellule REPL puis l'exécuter avec la combinaison de touches ++"⇑ Maj."+"Entrée ↵"++...

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
  </py-inputbox> -->

### `<py-box>`




### `<py-button>`

  <!-- <py-button label="Click me" styles="btn big">
def on_click(event):
    print(event)
  </py-button> -->



### `<py-config>`


