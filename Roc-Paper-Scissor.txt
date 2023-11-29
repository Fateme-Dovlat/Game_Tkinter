from tkinter import *
from tkinter import messagebox

rating_p1=0
rating_p2=0
def btnClick_1(string):
    global pl1
    pl1 = string
    text_input_1.set(string)

def btnClick_2(string):
    global  pl2
    pl2=string
    text_input_2.set(string)

def btnClick_3():
    global pl1
    global pl2
    global rating_p1
    global rating_p2

    p1 = PlayerOne(pl1)
    p2 = PlayerOne(pl2)
    if p1.rock == 'rock' and p2.scissor == 'scissor':
        rating_p1 = rating_p1+1
    elif p1.rock == 'rock' and p2.paper == 'paper':
        rating_p2 = rating_p2+1
    elif p1.paper == 'paper' and p2.rock == 'rock':
        rating_p1 = rating_p1+1
    elif p1.paper == 'paper' and p2.scissor == 'scissor':
        rating_p2 = rating_p2+1
    elif p1.scissor == 'scissor' and p2.paper == 'paper':
        rating_p1 = rating_p1+1
    elif p1.scissor == 'scissor' and p2.rock == 'rock':
        rating_p2 = rating_p2+1
    else:
        print("equal")
    text_input_3.set(rating_p1)
    text_input_4.set(rating_p2)

def btnClick_4():
    global a1, t,b1
    a1 = a.get()
    b1 = b.get()
    if rating_p1 > rating_p2:
        t=str(a1)+" is win  "
        messagebox.showinfo("result",t )
    elif rating_p1 < rating_p2:
        t = str(b1) + " is win  "
        messagebox.showinfo("result", t)
    else:
        t=str(a1)+" and "+str(b1)+" equaled "
        messagebox.showinfo("result", t)

class PlayerOne:
    def __init__(self,text_input_1):
        self.rock=text_input_1
        self.paper=text_input_1
        self.scissor=text_input_1

class PlayerTwo:
    def __init__(self,text_input_2):
        self.rock=text_input_2
        self.paper=text_input_2
        self.scissor=text_input_2
rps = Tk()
rps.title("Rock-Paper-Scissor")

Label(rps, text="     player 1",font=('arial', 20, 'bold'),foreground='blue').grid(row=2,column=0)
Label(rps, text=" Rating",font=('arial', 20, 'bold'),foreground='blue').grid(row=5,column=0)
Label(rps, text="     player 2",font=('arial', 20, 'bold'),foreground='green').grid(row=2,column=5)
Label(rps, text=" Rating",font=('arial', 20, 'bold')).grid(row=5,column=7)

a=StringVar()
e1 = Entry(rps,font=('arial', 10, 'bold'),textvariable = a, bd=20,
           insertwidth=4, bg='lightblue', justify='center').grid(row=2, column=1)
b=StringVar()
e2 = Entry(rps,font=('arial', 10, 'bold'),textvariable = b, bd=20,
           insertwidth=4, bg='lightgreen', justify='center').grid(row=2, column=6)

text_input_1 = StringVar()
txtDisplay_1= Entry(rps, font=('arial', 10, 'bold'), textvariable=text_input_1, bd=20,
                   insertwidth = 4, bg='lightblue', justify='center').grid(row=3, column=1)
btn_rock = Button(rps, padx=16, pady=16, bd=8, fg='black', font=('arial', 20, 'bold'),foreground='blue',
              text='  ROCK  ', command=lambda:btnClick_1("rock") ).grid(row=4, column=1)
btn_paper = Button(rps, padx=20, pady=16, bd=8, fg='black', font=('arial', 20, 'bold'),foreground='blue',
              text=' PAPER ', command=lambda:btnClick_1("paper")).grid(row=5, column=1)
btn_scissor = Button(rps, padx=16, pady=16, bd=8, fg='black', font=('arial', 20, 'bold'),foreground='blue',
              text='SCISSOR', command=lambda:btnClick_1("scissor")).grid(row=6, column=1)


text_input_2 = StringVar()
txtDisplay_2 = Entry(rps, font=('arial', 10, 'bold'), textvariable=text_input_2, bd=20,
                   insertwidth=4, bg='lightgreen', justify='center').grid(row=3, column=6)
btn_rock = Button(rps, padx=16, pady=16, bd=8, fg='black', font=('arial', 20, 'bold'),foreground='green',
              text='  ROCK  ', command=lambda:btnClick_2("rock")).grid(row=4, column=6)
btn_paper = Button(rps, padx=16, pady=16, bd=8, fg='black', font=('arial', 20, 'bold'),foreground='green',
              text=' PAPER ', command=lambda:btnClick_2("paper")).grid(row=5, column=6)
btn_scissor = Button(rps, padx=16, pady=16, bd=8, fg='black', font=('arial', 20, 'bold'),foreground='green',
              text='SCISSOR', command=lambda:btnClick_2("scissor")).grid(row=6, column=6)

btn_result = Button( rps,padx=16, pady=16, bd=8, fg='black', font=('arial', 20, 'bold'),foreground='red',
              text='RESULT', command=btnClick_3).grid(row=9,column=5)

btn_result_final = Button( rps,padx=16, pady=16, bd=8, fg='black', font=('arial', 20, 'bold'),foreground='red',
              text='RESULT FINAL', command=btnClick_4).grid(row=10,column=5)

text_input_3 = StringVar()
txtDisplay_3= Entry(rps, font=('arial', 10, 'bold'), textvariable=text_input_3, bd=20,
                   insertwidth=4, bg='powder blue', justify='center').grid(row=6, column=0)

text_input_4 = StringVar()
txtDisplay_4= Entry(rps, font=('arial', 10, 'bold'), textvariable=text_input_4, bd=10,
                   insertwidth=2, bg='green', justify='center').grid(row=6, column=7)

rps.mainloop()








