# games-library

 scrivere un programma che permetta all'utente di scegliere fra tre diverse funzioni.
 ognuna permette di fare un gioco diverso. Le scelte che ha sono fra:
 - indovina il numero (il computer prova, e gli viene detto se è troppo alto, troppo basso o giusto --> https://www.practicepython.org/exercise/2015/11/01/25-guessing-game-two.html
 - sasso, carta, forbice --> https://www.practicepython.org/exercise/2014/03/26/08-rock-paper-scissors.html
 - non so il nome in italiano --> https://www.practicepython.org/exercise/2014/07/05/18-cows-and-bulls.html

Creiamo dei branches e poi uniamo

    prompt = '\t\t\t\t LIBRERIA DI GIOCHI'

    prompt += '\n\nLe opzioni sono:'
    prompt += '\nIndovina il numero --> Inserire 1'
    prompt += '\nSasso, carta, forbice --> Inserire 2'
    prompt += '\nBoh --> Inserire 3 \n\n--> '

    scelta = int(input(prompt))

    if scelta == 1:
        guess_the_number()
    
    if scelta == 2:
        paper_rock_scissors()

    if scelta == 3:
        boh()
