# Quiz-Game
# import required libraries 

import requests 

from bs4 import BeautifulSoup 

from win10toast import ToastNotifier 

  
# create an object to ToastNotifier class 

n = ToastNotifier() 

  
# define a function 

def getdata(url): 

    r = requests.get(url) 

    return r.text 

    

htmldata = getdata("https://weather.com/en-IN/weather/today/l/25.59,85.14?par=google&temp=c/") 

  

soup = BeautifulSoup(htmldata, 'html.parser') 

  

current_temp = soup.find_all("span", class_= "_-_-components-src-organism-CurrentConditions-CurrentConditions--tempValue--MHmYY") 

  

chances_rain = soup.find_all("div", class_= "_-_-components-src-organism-CurrentConditions-CurrentConditions--precipValue--2aJSf") 

  

temp = (str(current_temp)) 

  

temp_rain = str(chances_rain) 

   

result = "current_temp " + temp[128:-9] + "  in patna bihar" + "\n" + temp_rain[131:-14] 

n.show_toast("live Weather update",  

             result, duration = 10) import random
# library that we use in order to choose 
# on random words from a list of words
 

name = input("What is your name? ")
# Here the user is asked to enter the name first
 

print("Good Luck ! ", name)
 

words = ['rainbow', 'computer', 'science', 'programming', 

         'python', 'mathematics', 'player', 'condition', 

         'reverse', 'water', 'board', 'geeks'] 
 
# Function will choose one random
# word from this list of words

word = random.choice(words)
 
 

print("Guess the characters")
 

guesses = ''
 
# any number of turns can be used here

turns = 12
 
 

while turns > 0:

     

    # counts the number of times a user fails

    failed = 0

     

    # all characters from the input

    # word taking one at a time.

    for char in word: 

         

        # comparing that character with

        # the character in guesses

        if char in guesses: 

            print(char)

             

        else: 

            print("_")

             

            # for every failure 1 will be

            # incremented in failure

            failed += 1

             
 

    if failed == 0:

        # user will win the game if failure is 0

        # and 'You Win' will be given as output

        print("You Win") 

         

        # this print the correct word

        print("The word is: ", word) 

        break

     

    # if user has input the wrong alphabet then

    # it will ask user to enter another alphabet

    guess = input("guess a character:")

     

    # every input character will be stored in guesses 

    guesses += guess 

     

    # check input with the character in word

    if guess not in word:

         

        turns -= 1

         

        # if the character doesn’t match the word

        # then “Wrong” will be given as output 

        print("Wrong")

         

        # this will print the number of

        # turns left for the user

        print("You have", + turns, 'more guesses')

         

         

        if turns == 0:

            print("You Loose")
