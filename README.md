# GUI-Restaurant-bill
from tkinter import *
import tkinter.messagebox

class Application(Frame):
    """ A GUI application displays a restaurant bill with tip options. """
    def __init__(self, master):
        super(Application,self).__init__(master)
        self.grid()
        self.create_widgets()

    def create_widgets(self):
        """ create widgets for restaurant bill tips. """
        Label(self, font=("adobe caslon pro italic",20,"bold"), text = "Select an appetizer"
              ).grid(row = 0, column = 0, sticky = W)
        
        Label(self,font=("adobe caslon pro italic",20,"bold"), text = "Select an entree"
              ).grid(row = 0, column = 1, sticky = W)

                
        Label(self, font=("adobe caslon pro italic",20,"bold"), text = "Select a dessert"
              ).grid(row = 0, column = 2, sticky = W)


        # APPETIZER
        self.app = StringVar()
        self.app.set(0)

        Radiobutton(self, text = "shrimp and veggie tempura: $12.99",
                    variable = self.app,
                    value = 12.99,
                    command = self.update_text
                    ).grid(row = 2, column = 0, sticky = W)
        Radiobutton(self, text = "wakame salad: $8.99",
                    variable = self.app,
                    value = 8.99,
                    command = self.update_text
                    ).grid(row = 3, column = 0, sticky = W)
        Radiobutton(self, text = "Edamame: $14.99",
                    variable = self.app,
                    value = 14.99,
                    command = self.update_text
                    ).grid(row = 4, column = 0, sticky = W)

        # ENTREE
        self.entree = StringVar()
        self.entree.set(0)

        Radiobutton(self, text = "Dashi Udon: $14.99",
                    variable = self.entree,
                    value = 14.99,
                    command = self.update_text
                    ).grid(row = 2, column = 1, sticky = W)
        Radiobutton(self, text = "Unagi: $21.99",
                    variable = self.entree,
                    value = 21.99,
                    command = self.update_text
                    ).grid(row = 3, column = 1, sticky = W)

        # DESSERT
        self.dessert = StringVar()
        self.dessert.set(0)

        Radiobutton(self, text = "Sticky Mango Rice: $7.99",
                    variable = self.dessert,
                    value = 7.99,
                    command = self.update_text
                    ).grid(row = 2, column = 2, sticky = W)
        Radiobutton(self, text = "Green Tea Ice Cream: $5.99",
                    variable = self.dessert,
                    value = 5.99,
                    command = self.update_text
                    ).grid(row = 3, column = 2, sticky = W)

        
        # results textbox
        self.results_txt = Text(self, width = 40, height = 5, wrap = WORD)
        self.results_txt.grid(row = 5, column = 0, columnspan = 3)
        
                    
    def update_text(self):
        """Update text widget and display choices """
        total_price =   float(self.app.get())+ float(self.entree.get()) + float(self.dessert.get())

        user_message = "Your total price: $" + str(total_price)
                              
        self.results_txt.delete(0.0, END)
        self.results_txt.insert(0.0, user_message)
        

root = Tk()
root.title("Menu")
app = Application(root)
root.mainloop()
