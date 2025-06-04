import csv

#Hier importeer ik de 2 csv bestanden
bestandNieuw = "Klanten-nieuw.csv"
bestandOud = "Klanten-oud.csv"

klantenNieuw = []
klantenOud = []

#Hier vergelijkt die bestandNieuw met bestandOud en haalt die de verschillen er tussen uit
with open(bestandNieuw, 'r') as klantenNieuwObj:
    klantenObjCsv = csv.reader(klantenNieuwObj,delimiter=';')
    headerNieuw = next(klantenObjCsv)
    for rij in klantenObjCsv:
        klantenNieuw.append(rij)

with open(bestandOud, 'r') as klantenOudObj:
    klantenOudObjCsv = csv.reader(klantenOudObj,delimiter=';')
    headerOud = next(klantenOudObjCsv)
    for rij in klantenOudObjCsv:
        klantenOud.append(rij)

#Hier print die als het al een bestande klant is en als dat niet zo is dat het een nieuwe klant is
for line in klantenNieuw:
    for lineOud in klantenOud:
        if line[6] == lineOud[6]:
            # print(f"{line} is een bestaande klant")	
            break
    else:
        print(f"{line} is een nieuwe klant")
