# games-library

 scrivere un programma che permetta all'utente di scegliere fra tre diverse funzioni.
 ognuna permette di fare un gioco diverso. Le scelte che ha sono fra:
 - indovina il numero (il computer prova, e gli viene detto se è troppo alto, troppo basso o giusto --> https://www.practicepython.org/exercise/2015/11/01/25-guessing-game-two.html
 - sasso, carta, forbice --> https://www.practicepython.org/exercise/2014/03/26/08-rock-paper-scissors.html
 - non so il nome in italiano --> https://www.practicepython.org/exercise/2014/07/05/18-cows-and-bulls.html

 Creiamo dei branches per risolverle e poi uniamo

    def guess_the_number():  # crea la funzione

        import random  # importa la libreria per generare numeri a random

        prompt = '\n\n\t\t\t\tINDOVINA IL NUMERO'
        prompt += '\n\nDato un numero compreso fra 1 e 100 conosciuto solo dal computer, prova ad indovinarlo.'
        prompt += '\nSe il numero che inserisci sarà troppo grande o troppo piccolo, '
        prompt += '\nti verrà dato un indizio sulla strada giusta.'
        prompt += '\n\nSe si desidera smettere inserire -1 '
        prompt += '\n\n\t\t\t\t\t\t\t\t\t\t\t Buona fortuna!'
        print(prompt)  # crea il messaggio da stampare inizialmente (i print multilinea vengono sfasati ed è più leggibile)

        num = random.randint(0, 100)  # numero del computer, casuale
        guess = -2  # variabile del giocatore inizializzata ad un numero che sarà sempre diverso da quello del computer
        active = True  # serve per far andare avanti il ciclo while
        max_numbers, min_numbers = [], []  # liste in cui verranno inseriti i numeri sbagliati già inseriti
        max_number, min_number = -1, -1  # numeri fra cui il valore è compreso inizializzati a valori sempre diversi da quelli possibili

        while active:

            guess = int(input('Inserire il numero. --> '))  # l'utente inserisce il valore e la variabile assume significato

            if guess == num:  # se l'utente indovina viene stampato un messaggio e il ciclo finisce
                print(f'\n\nCongratulazioni, hai indovinato. \nIl numero era {guess}')
                break

            elif guess == -1:  # se l'utente dice che vuole smettere ( = -1), il ciclo finisce
                break

            elif guess > num and num in max_numbers:  # se il numero inserito è maggiore del numero generato ed è già stato inserito,
                print('Il numero è già stato scelto \n (è troppo alto)')  # viene stampato un messaggio

            elif guess > num:  # se il numero inserito è maggiore di num viene stampato un messaggio diverso
                print('Il numero è troppo alto...')
                max_numbers.append(guess)  # il numero viene aggiunto alla lista dei numeri maggiori di num

            elif guess < num and num in min_numbers:  # se il numero inserito è minore del numero generato ed è già stato inserito,
                print('Il numero è già stato scelto \n (è troppo piccolo)')  # viene stampato un messaggio

            elif guess < num:  # se il numero inserito è minore di num viene stampato un messaggio diverso
                print('Il numero è troppo piccolo...')
                min_numbers.append(guess)  # il numero viene aggiunto alla lista dei numeri minori di num

            if max_numbers:  # se la lista dei numeri inseriti (sbagliati) maggiori di num ha degli elementi
                max_number = min(max_numbers)  # max_number diventa il numero più piccolo in essa (è il più vicino a num)
            if min_numbers:  # se la lista dei numeri inseriti (sbagliati) minori di num ha degli elementi
                min_number = max(min_numbers)  # min_number diventa il numero più grande in essa (è il più vicino a num)

            if min_number >= 0 and max_number >= 0:  # se sono maggiori di zero (significa che il -1 iniziale è stato rimpiazzato da un valore vero)
                print(f'il numero è compreso fra {min_number} e {max_number}')  # viene stampato un indizio
            elif max_number >= 0:  # se solo uno dei due è stato inserito
                print(f'il numero è minore di {max_number}')  # viene stampato un indizio che comprede solo una variabile
            elif min_number >= 0:
                print(f'il numero è maggiore di {min_number}')

        print('\n\nGrazie per aver giocato!')  # messaggio di ringraziamento finale


    guess_the_number()  # viene richiamata la funzione per farlo partire
    
    
    
    
