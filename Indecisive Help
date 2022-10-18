import random

class indecisive_help(object):

    def __init__(self, answers=[]):
        'the constructor'
        if len(answers)==0:

            answers.append('It is certain')
            answers.append('It is decidedly so')
            answers.append('Without a doubt')
            answers.append('Yes definitely')
            answers.append('You may rely on it')
            answers.append('As I see it, yes')
            answers.append('Most likely')
            answers.append('Outlook good')
            answers.append('Yes')
            answers.append('Signs point to yes')
            answers.append('Reply hazy try again')
            answers.append('Ask again later')
            answers.append('Better not tell you now')
            answers.append('Cannot predict now')
            answers.append('Concentrate and ask again')
            answers.append("Don't count on it")
            answers.append('My reply is no')
            answers.append('My sources say no')
            answers.append('Outlook not so good')
            answers.append('Very doubtful')

        self.answers=answers
        self.shake()

    def shake(self):
        'get the next answer'
        self.current=random.randrange(0,len(self.answers))

    def get(self):
        'get the current answer'
        return self.answers[self.current]

    def numAnswers(self):
        'get the number of answers in the ball'
        return len(self.answers)

    def __iter__(self):
        'get the iterator'
        return iter(self.answers)

    def __str__(self):
        'string representation'
        return f'I am decisive program that helps the user stop being indecisive with {self.numAnswers()} answers. '

from tkinter import Button, Entry, Label,Tk, END
from tkinter.messagebox import showinfo

class indecisive_help(Tk):

    def __init__(self,ball=indecisive_help(),parent=None):
        Tk.__init__(self, parent)
        self.ball=ball
        self.title('Indecisive Help, Decisions Made For You!')
        self.make_widgets()

    def shake(self):
        self.ball.shake()
        showinfo(title='Im shaking', message='I am searching the mystic realms (RAM) for an answer...')
    
    def askQuestion(self):
        answer=self.ball.get()
        question=self.entry.get()
        showinfo(title='The answer... ', message= f'The answer to your question {question} is {answer}. ')
        self.entry.delete(0,END)

    def make_widgets(self):
        Label(self,text='Please ask a question: ').grid(row=0,column=0)
        self.entry=Entry(self,width=40)
        self.entry.grid(row=1,column=0)

        Button(self,text='Search for the answer', command=self.shake).grid(row=2,column=0)
        Button(self,text='The Decision', command=self.askQuestion).grid(row=3,column=0)

snarkyAnswers=['I dont care','leave me alone','buzz off','what do you want again?']
    
indecisive_help().mainloop()
