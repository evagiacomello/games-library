# games-library

 scrivere un programma che permetta all'utente di scegliere fra tre diverse funzioni.
 ognuna permette di fare un gioco diverso. Le scelte che ha sono fra:
 - indovina il numero (il computer prova, e gli viene detto se è troppo alto, troppo basso o giusto --> https://www.practicepython.org/exercise/2015/11/01/25-guessing-game-two.html
 - sasso, carta, forbice --> https://www.practicepython.org/exercise/2014/03/26/08-rock-paper-scissors.html
 - non so il nome in italiano --> https://www.practicepython.org/exercise/2014/07/05/18-cows-and-bulls.html

=======
 Creiamo dei branches per risolverle e poi uniamo

    import random
    
    def sasso_carta_forbice():

    print('\nPAPER ROCK SCISSORS')

    prompt = "\n\nCiao, giochiamo a sasso, carta, forbice! \nQuello che devi fare è immettere la tua scelta (sasso, carta, forbice), '"
    prompt += "\nE il computer giochera contro di te\n Inserisci 'q' per abbandonare"
    print(prompt)

    user_count, computer_count = 0, 0
    user_values = {'carta': 1, 'Carta': 1, 'sasso': 2, 'Sasso': 2, 'forbice': 3, 'Forbice': 3}
    computer_values = {1: 'carta', 2: 'sasso', 3: 'forbice'}  # dizionario di corrispondenze

    while True:

        while True:

            num = random.randint(1, 3)  # estrazione di ciò che gioca il computer
            user = input('\n\nInserisci cosa giochi: ')

            if user in user_values:  # riassenazione delle stringhe inserite dall'utente
                user = user_values[user]
            else:
                print('Invalid syntax')
                continue

            print(f'Il computer gioca {computer_values[num]}')

            if user == num:  # definizione dei punti
                print("Pareggio!")
            elif (user == 1 and num == 2) or (user == 2 and num == 3) or (user == 3 and num == 1):
                print('Hai vinto una partita! + 1pt')
                user_count += 1  # aumento del contatore per i punti del match
            else:
                print('Il computer ha vinto una partira! + 1pt per il computer!')
                computer_count += 1

            if computer_count == 3 or user_count == 3:  # se qualcuno è arrivato a tre si smette
                break

        if computer_count > user_count:  # display dei punti finali
            choice = int(input(f"\n\nIl computer ha vinto {computer_count} a {user_count}. \nVuoi fare un'altra partita? Yes=0, No=1 --> "))

        else:
            choice = int(input(f"\n\nHai vinto {user_count} a {computer_count}. \nVuoi fare un'altra partita? Yes=0, No=1 --> "))

        user_count, computer_count = 0, 0  # punti di nuovo a zero

        if choice == 1:
            break
            
            
    def guess_the_number():  # crea la funzione

        prompt = '\n\n\t\t\t\tINDOVINA IL NUMERO'
        prompt += '\n\nDato un numero compreso fra 1 e 100 conosciuto solo dal computer, prova ad indovinarlo.'
        prompt += '\nSe il numero che inserisci sarà troppo grande o troppo piccolo, '
        prompt += '\nti verrà dato un indizio sulla strada giusta.'
        prompt += '\n\nSe si desidera smettere inserire -1 '
        prompt += '\n\n\t\t\t\t\t\t\t\t\t\t\t Buona fortuna!'
        print(prompt)  

        num = random.randint(0, 100)  # numero del computer, casuale
        max_numbers, min_numbers = [], []  # liste in cui verranno inseriti i numeri sbagliati già inseriti
        max_number, min_number = -1, -1  # numeri fra cui il valore è compreso inizializzati a valori sempre diversi da quelli possibili

        while True:

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
                

    prompt = '\t\t\t\t LIBRERIA DI GIOCHI'

    prompt += '\n\nLe opzioni sono:'
    prompt += '\nIndovina il numero --> Inserire 1'
    prompt += '\nSasso, carta, forbice --> Inserire 2'
    prompt += '\nBoh --> Inserire 3 \n\n--> '

    scelta = int(input(prompt))

    if scelta == 1:
        guess_the_number()  # viene richiamata la funzione per farlo partire
    
    if scelta == 2:
        sasso_carta_forbice()

    # if scelta == 3:
        # boh()
        
    print('\n\nGrazie per aver giocato!')  # messaggio di ringraziamento finale
   
