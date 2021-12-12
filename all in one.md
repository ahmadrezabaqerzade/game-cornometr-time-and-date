# game-cornometr-time-and-date
#all cornometr and game and showing date and time in one program
import time
import datetime
import json
import os
address1='newgame.json'
address2='time.json'
address3="name's.json"

#1 checked
def counter():
    print("\n"*3)
    time.sleep(0.5)
    print("if you want to start the countdown press     *inv*")
    time.sleep(0.4)
    print("if you want to start count press             *count*")
    time.sleep(0.4)
    print("if you want exit press                       *quit*")
    print('\n'*3)
    time.sleep(0.4)
    key=input()
    if key=='inv':
        def inv():
            print("specify a few second")
            seconds=input()
            second=seconds
            try:
                seconds=int(second)
                def inv_count():
                    print("select the counting speed::::")
                    sel=input()
                    try:
                        sel=int(sel)
                        def speed():
                            print('\n'*2)
                            for l in range(int(second)+1):
                                print(f"*******  {int(second)-l}  *******")
                                time.sleep(1/int(sel))
                            print("      **DONE**")
                            print('\n'*3)
                            time.sleep(0.3)
                            counter()
                        speed()
                    except ValueError:
                            print("*choose integer just*")
                            time.sleep(0.3)
                            inv_count()
                        
                inv_count()
                    
            except ValueError:
                print('\n'*2)
                time.sleep(0.3)
                print("***enter number not else***")
                print('\n')
                inv()
        inv()
    elif key=='count':
        def count():
            print("specify a few second")
            seconds=input()
            second=seconds
            try:
                seconds=int(second)
                def d_count():
                    print("select the counting speed::::")
                    sel=input()
                    try:
                        sel=int(sel)
                        def speed1():
                            print('\n'*2)
                            for l in range(int(second)+1):
                                print(f"*******  {l}  *******")
                                time.sleep(1/int(sel))
                            print("      **DONE**")
                            print('\n'*3)
                            time.sleep(0.3)
                            counter()
                        speed1()
                    except ValueError:
                            print("*choose integer just*")
                            time.sleep(0.3)
                            d_count()
                        
                d_count()
                    
            except ValueError:
                print('\n'*2)
                time.sleep(0.3)
                print("***enter number not else***")
                print('\n')
                count()
        count()
#2 checked
def date_and_time():
    print('\n'*3)
    time.sleep(0.9)
    print("if you want to see date press                     *date*     ")
    time.sleep(0.4)
    print("if you want to see a day of week press            *day*      ")
    time.sleep(0.4)
    print("if you want to see time press                     *time*     ")
    time.sleep(0.3)
    print("if you want to see both of them together press     *td*")
    time.sleep(0.4)
    print("if exit this part press                           *quit*     ")
    key=input()
    print('\n'*2)
    time.sleep(0.4)
    if key=='date':
        print(datetime.date.today())
        date_and_time()
    elif key=='day':
        print(datetime.datetime.now().strftime('%A'))
        date_and_time()
    elif key=='time':
        print(time.strftime("%H:%M:%S", time.localtime()))
        date_and_time()
    elif key=='td':
        print(time.ctime(time.time()))
        date_and_time()
    elif key=='quit':
        return None
    else:
        print("*wrong key try again*")
        date_and_time()
        
#3
def made_file(number_list,address):
    with open(address,'w') as w:
        json.dump(number_list,w)
    with open(address) as r:
        number_list=json.load(r)
    return number_list


#4
def open_file(address):
    with open(address) as r:
        number_list=json.load(r)
    return number_list

#5
def game():
        #5-1
        def check_word(i):
            def check_word1():
            
                "checking recived names"
                print(f"enter your word:::{i}'s word")
                word='a'
                del(word)
                word=input()

                word_right='abcdefghijklmnopqrstuvwxyz'
                repeat_word=[]
                with open(address1,'r') as r:
                    rep=json.load(r)
                    size=len(rep["0"])
                    
                    for u in range(size):
                        
                        for j in range(len(rep)):
                            lists=rep[str(j)]
                            
                            try:
                                repeat_word.append(lists[u])
                            except IndexError:
                                None

                for p in list(word):
                    
                    if p in word_right:
                        None
                        
                    else:
                        print("*you can write just with small letter*")
                        print('\n'*2)
                        time.sleep(0.3)
                        word=check_word1()
                        
                if word in repeat_word:
                    print('\n'*2)
                    print("**rarly word**")
                    print('\n'*2)
                    print("enter new word:::")
                    word=check_word1()
                else:
                    if len(repeat_word)==0:
                        None
                        return word
                        
                        
                    else:
                        letter1=word[0]
                        word1=repeat_word[-1]
                        letter2=word1[-1]
                        
                        if letter1==letter2:
                                None
                                return word
                        else:
                            print(repeat_word)
                            print('\n'*3)
                            print(f"a word must be started {letter2}")
                            word=check_word1()
             
     
                print('\n'*2)
                time.sleep(0.4)
                print("*success*")
                return word
            word=check_word1()
            return word
        #5-2
        def gamer_name():
            "to getting the gamer name by dictionarie's and saving them in json's file"
            print("inter the number of gamer")
            number=input()
            try:
                number=int(number)
                number_list={}
                number_list1=[]
                for i in range(number):
                    def save():
                        "saving gamer name in dicttionary"
                        print(f"enter a gamer{i+1} name")
                        gamer_name=input()
                        if gamer_name in number_list1:
                            print("*the name is rarly please enter a new name*")
                            print('\n'*2)
                            time.sleep(0.3)
                            save()
                        else:
                            number_list[i]=[]
                            number_list1.append(gamer_name)
                            with open(address3,'w') as w:
                                json.dump(number_list1,w)
                        return number_list
                    save()
            except ValueError:
                print("*the number must be integer*")
                gamer_name()
            number_list=number_list
            return number_list
        
        #5-3
        def gamer_word(number_list,i,address1):
            "adding a word to gamer"
            with open(address2) as r:
                time_list=json.load(r)
            t1=time.time()
            word=check_word(i)
            number_list[i].append(word)
            t2=time.time()
            time_list.append(t2-t1)
            with open(address2,'w') as w:
                json.dump(time_list,w)
            made_file(number_list,address1)
            return number_list
        #5-4
        def score(number_list):
            for i in range(number_list):
                print(f"{number_list[i]}::: {len(number_list[i])}")
                time.sleep(0.2)
            
        def start_game():
            key='a'
            while(key!='quit'):
                print('\n'*3)
                print("for new game press-------------------------------------->>> new <<<")
                time.sleep(0.3)
                print("for seeing date and time press-------------------------->>> dat <<<")
                time.sleep(0.3)
                print("for usin cornometr press-------------------------------->>> count <<<")
                time.sleep(0.3)
                print("for exit this program press----------------------------->>> quit <<<")
                
                key=input()
                
                if key=='new':
                    time_list=[]
                    with open(address2,'w') as w:
                        json.dump(time_list,w)
                    print('\n'*2)
                    def n_times():
                        print("how many time's do you play???:::::::")
                        n=input()
                        if type(int(n)) is int:
                            n=int(n)
                            return n
                        else:
                            print("**enter integer**")
                            n_times()
                    s=n_times()
                    number_list=gamer_name()
                    for i in range(len(made_file(number_list,address1))):
                        lim=gamer_word(number_list,i,address1)
                    for j in range(s-1):
                        for i in range(len(made_file(number_list,address1))):
                            lim=gamer_word(number_list,i,address1)
                           
                    with open(address2,'r') as r:
                        time1=json.load(r)
                        
                    n=len(lim)  
                    score=[]
                    
                    for k in range(s):
                        times=0
                        for l in range(n):
                            times+=time1[l*n+k]
                        score.append(times)
    
                        
                    with open(address3,'r') as r:
                        name=json.load(r)
                        
                    free={}
                    print('\n'*5)
                    for i in range(n):
                        print(f"{name[i]}'s time is :::: {score[i]}  seccond")
                        time.sleep(0.5)
                        free[score[i]]=name[i]
                        
                    print('\n')
                    for i in range(n):
                        print(f"{free[min(score)]}'s place------>>{i+1} ")
                        time.sleep(0.5)
                        score.remove(min(score))
                        
                    time.sleep(0.6)
                    print('\n'*3)
                    os.remove(address1)
                    os.remove(address2)
                    os.remove(address3)
                    
                elif key=='dat':
                    date_and_time()
                
                elif key=='count':
                    counter()
                
                elif key=='quit':
                    break 
                
                else:
                    print("**wrong key**")
                    
        start_game()
        
            
game()
