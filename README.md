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
