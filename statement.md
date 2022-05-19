# Welcome!

This Python template lets you get started quickly with a simple one-page playground.

```python runnable
import sys
import math
print("veuilles entrer la liste de W séparé par un espace exemple: 0.05 0.1 0.2\nA vous !")
# retirez le tableau et le '#' pour rentrer manuellement le poid 
w = input().split()

# initialisation de la variable de la sortie
y=0

# liste d'entrée
entree = [["100",0],["101",0],["111",1],["110",0]]

print("indiquez le nu:")
# retirez la valeur et le '#' pour rentrer manuellement le nu
nu = float(input())

# choix de l'entrée parmis le tableau 'entree'
#print("pour choisir une entrée merci de prendre la valeur associer à l'entrée:\n",entree[:])
index_entree = 0



def calcul_wixi(i):
    wixi = 0
    for a in range(len(entree[i])):
        wixi+=float(entree[i][0][a])*float(w[a])
    return wixi

def verif_y_cible(wixi,index_entree, entree):
    # Vérifie si la sortie du wixi (Y) est pareil à la cible
    if (wixi>0 and entree[index_entree][1]==1) or (entree[index_entree][1]==0 and wixi<0):
        print("Correct !")
    else:
        print("Incorrect !")

def ajustement_poids(nu,entree,index_entree,y,w):
    # Pour chaque W on applique la formule nu*(Y-cible)*W[i]+entree[i]
    for i in range(2):
        cible = entree[index_entree][1]
        w[i]=nu*(cible-y)*float(entree[index_entree][0][i])+float(w[i])

print("[",sep="",end="")
for i in range(100):
    index_entree+=1
    if index_entree>3:
        index_entree=0
    # 1er étape calcul du WIXI
    wixi = calcul_wixi(index_entree)
    #print("wixi =",wixi,"\nentree: ",entree[index_entree])

    # On assigne Y
    if wixi>0:
        y=1
    else:
        y = 0

    # Vérifie si la sortie est correct (Y == cible)
    # verif_y_cible(wixi,index_entree, entree)

    #print("ancien poids: ",w[:])
    # On calcul les nouveaux poids
    ajustement_poids(nu,entree,index_entree,y,w)
    print("#",end="")
print("] 100%")
print("Phase d'apprentissage terminée")
print("nouveau poids: ",w[:])




```

# Advanced usage

If you want a more complex example (external libraries, viewers...), use the [Advanced Python template](https://tech.io/select-repo/429)
