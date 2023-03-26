# Cas6


import psycopg2 as psycopg2

try:
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor() 
    com='''CREATE TABLE DOSTAVLJAC (
        ID_DOSTAVLJACA SERIAL PRIMARY KEY NOT NULL, 
        IME_PREZIME VARCHAR (30) NOT NULL
        );
        '''
    cursor.execute(com)
    print ("Tabela je uspesno formirana")
    con.commit() #snima se promena
except (Exception,psycopg2.Error) as e:
    print("Error",e)

finally:               
    if con:
        cursor.close()
        con.close()
 # zadatak2
        
==========================================        
        
import psycopg2 as psycopg2

try:
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor() 
    l=['''INSERT INTO DOSTAVLJAC (IME_PREZIME) VALUES ('VELJKO KRSTIC') 
    ''',
    '''INSERT INTO DOSTAVLJAC (IME_PREZIME) VALUES ('MARKO MILIC') 
    ''',
    '''INSERT INTO DOSTAVLJAC (IME_PREZIME) VALUES ('SOFIJE NIKIC') 
    ''',
    '''INSERT INTO DOSTAVLJAC (IME_PREZIME) VALUES ('MATIJA RADIC') 
    '''
     ]
    for i in l:
        cursor.execute(i)
    con.commit() 
except (Exception,psycopg2.Error) as e:
    print("Error",e)
finally:               
    if con:
        cursor.close()
        con.close()

#zadatak 3
====================================
import psycopg2 as psycopg2

def funkcija_all():
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor()
    cursor.execute("SELECT * FROM DOSTAVLJAC")
    result=cursor.fetchall()
    cursor.close()
    con.close()
    print(result)


def funkcija_many():
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor()
    cursor.execute("SELECT * FROM DOSTAVLJAC") #''' se stavlja samo ako naredba mora u vise redova
    result=cursor.fetchmany(2)
    print(result)
    result=cursor.fetchmany(2)
    cursor.close()
    con.close()
    print(result)


def funkcija_one():
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor()
    cursor.execute("SELECT * FROM DOSTAVLJAC")
    result=cursor.fetchone()
    cursor.close()
    con.close()
    print(result)
    

funkcija_all()
print('='*50)

funkcija_many()
print('='*50)

funkcija_one()
print('='*50)

===================================

import psycopg2 as psycopg2

try:
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor() 
    com='''CREATE TABLE PORUDZBINA (
        ID_PORUDZBINA SERIAL NOT NULL, 
        IME_PREZIME VARCHAR (30) NOT NULL,
        ADRESA VARCHAR (30) NOT NULL,
        RESTORAN VARCHAR (30) NOT NULL,
        IZNOS FLOAT NOT NULL,
        ID_DOSTAVLJACA INTEGER NULL,
        PRIMARY KEY (ID_PORUDZBINA),
        FOREIGN KEY (ID_DOSTAVLJACA) REFERENCES DOSTAVLJAC (ID_DOSTAVLJACA)
        );
        '''
    cursor.execute(com)
    print ("Tabela je uspesno formirana")
    con.commit()                            
except (Exception,psycopg2.Error) as e:
    print("Error",e)

finally:               
    if con:
        cursor.close()
        con.close()

=====================
zadatak5
import psycopg2 as psycopg2

try:
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor() 
    l=['''INSERT INTO PORUDZBINA (IME_PREZIME,ADRESA,RESTORAN,IZNOS,ID_DOSTAVLJACA) VALUES ('VELJKO KRSTIC','ADRESA 1','RESTORAN 1', 250,NULL) 
    ''',
    '''INSERT INTO PORUDZBINA (IME_PREZIME,ADRESA,RESTORAN,IZNOS,ID_DOSTAVLJACA) VALUES ('GORAN SOM','ADRESA 2','RESTORAN 2', 350,NULL) 
    ''',
    '''INSERT INTO PORUDZBINA (IME_PREZIME,ADRESA,RESTORAN,IZNOS,ID_DOSTAVLJACA) VALUES ('MILAN EDRT','ADRESA 3','RESTORAN 3', 1250,NULL) 
    ''',
    '''INSERT INTO PORUDZBINA (IME_PREZIME,ADRESA,RESTORAN,IZNOS,ID_DOSTAVLJACA) VALUES ('ZORAN MIE','ADRESA 4','RESTORAN 4', 2500,NULL) 
    ''',
    '''INSERT INTO PORUDZBINA (IME_PREZIME,ADRESA,RESTORAN,IZNOS,ID_DOSTAVLJACA) VALUES ('MILAN EDRT','ADRESA 5','RESTORAN 5', 12150,NULL) 
    ''',
     ]
    for i in l:
        cursor.execute(i)
    con.commit() 
except (Exception,psycopg2.Error) as e:
    print("Error",e)
finally:               
    if con:
        cursor.close()
        con.close()

================================
zadatak6
import psycopg2 as psycopg2

def funkcija_all():
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor()
    cursor.execute("SELECT * FROM PORUDZBINA")
    result=cursor.fetchall()
    cursor.close()
    con.close()
    print(result)

funkcija_all()
print('='*50)
====================================
zadata7
import psycopg2 as psycopg2

def funkcija_dodeli():
    con=psycopg2.connect(database='glovo',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor()
    cursor.execute('''UPDATE PORUDZBINA 
    SET ID_DOSTAVLJACA=1 WHERE ID_PORUDZBINA=1
    ''')
    con.commit()
    cursor.close()
    con.close()
funkcija_dodeli()
print('='*50)

============================================
zadatak8
import psycopg2 as psycopg2

try:
    con=psycopg2.connect(database='KUVAR',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor() 
    com='''CREATE TABLE RECEPT (
        ID_RECEPT SERIAL PRIMARY KEY NOT NULL, 
        NAZIV_RECEPT VARCHAR (30) NOT NULL,
        CENA FLOAT NOT NULL,
         PORCIJE INTEGER NOT NULL
        );
        '''
    cursor.execute(com)
    print ("Tabela RECEPATA je uspesno formirana")
    con.commit()                            
except (Exception,psycopg2.Error) as e:
    print("Error",e)

finally:               
    if con:
        cursor.close()
        con.close()

a=eval(input('Broj unosa: '))
for i in range (a):
    con=psycopg2.connect(database='KUVAR',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor()
    b=input('Unesite sledece podatke: naziv recepta, cenu i porcije: ')
    nazvr=b.split(',')[0]
    cena=(b.split(',')[1])
    porcija=(b.split(',')[2])
    com='''INSERT INTO RECEPT ('NAZIV_RECEPT',CENA,PORCIJE) VALUES ({},{},{}) 
    '''.format(nazvr,cena,porcija)
    cursor.execute(com)
    con.commit()
    cursor.close()
    con.close()




======================================
zadatak9
import psycopg2 as psycopg2

a=eval(input('Broj unosa: '))
for i in range (a):

    con=psycopg2.connect(database='KUVAR',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor()
    b=input('Unesite sledece podatke: naziv recepta, cenu i porcije: ')
    nazvr=b.split(',')[0]
    cena=(b.split(',')[1])
    porcija=(b.split(',')[2])
    com='''INSERT INTO RECEPT (NAZIV_RECEPT,CENA,PORCIJE) VALUES ('{}',{},{}) 
    '''.format(nazvr,cena,porcija)
    cursor.execute(com)
    con.commit()
    cursor.close()
    con.close()




===============================
zadatak10
import psycopg2 as psycopg2

def funkcija_all():
    con=psycopg2.connect(database='KUVAR',
    user='postgres',
    password='itoip',
    host='localhost',
    port='5432'
    )
    cursor=con.cursor()
    cursor.execute("SELECT * FROM RECEPT")
    result=cursor.fetchall()
    cursor.close()
    con.close()
    print(result)

l=funkcija_all()


for i in l:
    print("ID REcepta: {}".format(i[0]),file=f)
    print("ID REcepta: {}".format(i[1]),file=f)
    print("ID REcepta: {}".format(i[2]),file=f)
    print("ID REcepta: {}".format(i[3]),file=f)
f.close()


