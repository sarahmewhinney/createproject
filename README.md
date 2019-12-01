# createproject

#Sarah Mewhinney
#CSCI 101- Section B
#Create Project


numcards = 12
with open("setfile.txt", 'w') as setfile:
    print("please imput your set board as a instructed, your first character should be a 1, 2, or 3 depending on the number of objects on your card.")
    print("The next character should be r, p, or g for the color of the card red, purple, or green.")
    print("The next character should be o, s, or d this for the shapes that appear on your cards sqwiggle, oval or diamond.")
    print("The last character should be h, f, or b for the texture of your shapes either hashed, filled in or blank.")
    print("An example would be, a card with one purple squiggle that is filled in would be: 1psf")
    inputtedcards = input("enter your cards here with a space inbetween each card")
    setfile.write(inputtedcards) 



def FormSet(setfile):
    numcards = 12
    i = 0
    j = 1
    k = 2
    sets = []
    ultraset = []
    while i < numcards - 2:
        j = i + 1 
        while j < numcards - 1:
            k = j + 1
            while k < numcards:
                if (IsSet(setfile[i], setfile[j], setfile[k])) == True:
                    sets.append(setfile[i])
                    sets.append(setfile[j])
                    sets.append(setfile[k])
                k = k + 1
            j = j + 1 
        i = i + 1
    print("here are your sets: ps. the sets are listed in order so the first three strings are one set, the next three are another set and so on", sets)
                
def IsSet(card1, card2, card3):
    correct = []
    color = 1
    shape = 2
    texture = 3
    num = 0 
    if card1[color] == card2[color] == card3[color]:
        correct.append("color")
    elif (card1[color] != card2[color]) and (card1[color] != card3[color]) and (card3[color] != card2[color]):
        correct.append("color")
    if card1[shape] == card2[shape] == card3[shape]:
        correct.append("shape")
    elif (card1[shape] != card2[shape]) and (card1[shape] != card3[shape]) and (card3[shape] != card2[shape]):
        correct.append("shape")
    if card1[texture] == card2[texture] == card3[texture]:
        correct.append("texture")
    elif (card1[texture] != card2[texture]) and (card1[texture] != card3[texture]) and (card3[texture] != card2[texture]):
        correct.append("texture")
    if card1[num] == card2[num] == card3[num]:
        correct.append("num")
    elif (card1[num] != card2[num]) and (card1[num] != card3[num]) and (card3[num] != card2[num]):
        correct.append("num")
    if "color" in correct:
        if "num" in correct:
            if "texture" in correct:
                if "shape" in correct:
                    return True
                else:
                    return False
            else:
                return False
        else:
            return False
    else:
        return False
    
with open("setfile.txt", "r+") as setf:
    setfile = setf.readline()
    setfile = setfile.split()
    FormSet(setfile)
    
        

    
