# Library-management-system-
Implemented a Python Library Management System with book addition, viewing, searching, issuing, and returning features.
print("===== LIBRARY MANAGEMENT SYSTEM =====")

books = []

while True:
    print("\n1. Add Book")
    print("2. View Books")
    print("3. Search Book")
    print("4. Issue Book")
    print("5. Return Book")
    print("6. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        title = input("Enter book title: ")
        author = input("Enter author name: ")

        book = {
            "title": title,
            "author": author,
            "status": "Available"
        }

        books.append(book)

        print("Book added successfully!")

    elif choice == "2":
        print("\n===== BOOK LIST =====")

        if len(books) == 0:
            print("No books found.")
        else:
            for book in books:
                print("Title:", book["title"])
                print("Author:", book["author"])
                print("Status:", book["status"])
                print("-------------------")

    elif choice == "3":
        title = input("Enter book title to search: ")
        found = False

        for book in books:
            if book["title"].lower() == title.lower():
                print("\nBook Found!")
                print("Title:", book["title"])
                print("Author:", book["author"])
                print("Status:", book["status"])
                found = True
                break

        if not found:
            print("Book not found.")

    elif choice == "4":
        title = input("Enter book title to issue: ")
        found = False

        for book in books:
            if book["title"].lower() == title.lower():
                found = True

                if book["status"] == "Available":
                    book["status"] = "Issued"
                    print("Book issued successfully!")
                else:
                    print("Book is already issued.")

                break

        if not found:
            print("Book not found.")

    elif choice == "5":
        title = input("Enter book title to return: ")
        found = False

        for book in books:
            if book["title"].lower() == title.lower():
                found = True

                if book["status"] == "Issued":
                    book["status"] = "Available"
                    print("Book returned successfully!")
                else:
                    print("This book was not issued.")

                break

        if not found:
            print("Book not found.")

    elif choice == "6":
        print("Thank you for using Library Management System!")
        break

    else:
        print("Invalid choice!")
