[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=9228765&assignment_repo_type=AssignmentRepo)
# CODELAB-1


products_in_machine = [
    {
        "id": 0,
        "name": "icafe",
        'price': 5,
    },
    {
        "id": 1,
        "name": "cappuccino",
        'price': 25,
    },
    {
        "id": 2,
        "name": "hot chocolate",
        'price': 13,
    },
    {
        "id": 3,
        "name": "ice caramel",
        'price': 14,
    },
    {
        "id": 4,
        "name": "white mocha in spanish",
        'price': 8,
    },
    {
        "id": 5,
        "name": "tea",
        'price': 2,
    },
    {
        "id": 6,
        "name": "cinammon muffin",
        'price': 25,
    },
    {
        "id": 7,
        "name": "maplenut frappe",
        'price': 15,
    },
    {
        "id": 8,
        "name": "iced mappelnut latte",
        'price': 21,
    },
    {
        "id": 9,
        "name": "long coffee",
        'price': 12,
    },
    {
        "id": 10,
        "name": "short coffee",
        'price': 10,
    },
    {
        "id": 11,
        "name": "iced latte",
        'price': 20,
    },
]


items_purchased = []

receipt = """
\t\tPRODUCT -- PRICE
"""

sum = 0

run = True

print("Thanks for visiting the fast coffee vending machine\n\n")


for i in products_in_machine:
    print(f"""
    Item: {i['name']}  
    Price: {i['price']} 
    Item ID: {i['id']}
    """)


def machine(products_in_machine, run, items_purchased):
    while run:

        to_buy = int(input("\n\nPut the product's code into the box provided: "))

        if to_buy < len(products_in_machine):
            items_purchased.append(products_in_machine[to_buy])
            
        else:
            print("THE PRODUCT ID IS WRONG!")
        
        
        

        add_items = str(input("to add more things, hit any key, and to stop, press q.. "))

        if add_items == "q":
            run = False
        
        

    for_bill = int(input(("1. For the receipt 2. For your total .. ")))
    if for_bill == 1:
        print(create_receipt(items_purchased, receipt))
    elif for_bill == 2:
        print(sum(items_purchased))
    else:
        print("INVALID ENTRY")


def create_receipt(items_purchased, receipt):

    for i in items_purchased:
        receipt += f"""
        \t{i["name"]} -- {i['price']}
        """

    receipt += f"""
        \tTotal --- {sum(items_purchased)}
        
    
        
        """
   
    return receipt

def sum(items_purchased):
    sum = 0

    for i in items_purchased:
        sum += i["price"]

    return sum




if __name__ == "__main__":
    machine(products_in_machine, run, items_purchased)
   

    money = int(input("Enter the amount"))
    Total = 0


    for i in items_purchased:
        Total += i["price"]
    
    if Total == int(money):
        for i in items_purchased:
            print(f"Your {i['name']} has been distributed, so please pick it up")
            
    elif Total < int(money):
        Change1 = money - Total
        print("Your change is available for pickup" , Change1, "DHS")
        for i in items_purchased:
            print(f"Your {i['name']} is ready, Please pickup")
            
    elif Total > int(money):
        Change2 = Total - money
        print("Enter" , Change2, "DHS", "more")
        money = int(input("Insert the amount"))
        if Change2 == int(money):
            for i in items_purchased:
                print(f"Your {i['name']} is ready, Please pickup")
                
        elif Change2 < int(money):
            Change3 = money - Change2
            print("Your change is available for pickup,", Change3, "DHS")
        
    
    else:
        print("Insert the amount")
        money = int(input("Insert the amount"))
    print("Thank you, see you soon.")
