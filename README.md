# LMS
Library Management system based on Python ,mysql

from tkinter import *
from tkinter import ttk
import mysql.connector
from tkinter import messagebox
import tkinter
import datetime

class LibraryManagementSystem:
    def __init__(self,root):
        self.root=root
        self.root.title("Library Management System")
        self.root.geometry("1550x800+0+0")

        # ============ Variable ==================

        self.member_var=StringVar()
        self.prn_var=StringVar()
        self.id_var=StringVar()
        self.firstname_var=StringVar()
        self.lastname_var=StringVar()
        self.year_var=StringVar()
        self.branch_var=StringVar()
        self.email_var=StringVar()
        self.mobile_var=StringVar()
        self.bookid_var=StringVar()
        self.booktitle_var=StringVar()
        self.author_var=StringVar()
        self.dateborrowed_var=StringVar()
        self.datedue_var=StringVar()
        self.daysofbook_var=StringVar()
        self.latereturnfine_var=StringVar()
        self.dateoverdue_var=StringVar()
        self.finalprice_var=StringVar()

        # lbl_title=Label(self.root,text="LIBRARY MANAGEMENT SYSTEM",bg="RoyalBlue1",fg="RoyalBlue4",bd=20,relief=RIDGE,font=("times new roman",50,"bold"),padx=2,pady=6)
        lbl_title=Label(self.root,text="LIBRARY MANAGEMENT SYSTEM",bg="blue4",fg="snow",bd=20,relief=FLAT,font=("times new roman",50,"bold"),padx=2,pady=6)
        lbl_title.pack(side=TOP,fill=X)

        frame=Frame(self.root,bd=12,relief=RIDGE,padx=20,bg="SteelBlue1")
        frame.place(x=0,y=130,width=1536,height=400)

        #============ DataFrameLeft ==============

        DataFrameLeft=LabelFrame(frame,text="Library Membership Information",bg="SteelBlue2",fg="RoyalBlue4",bd=12,relief=RIDGE,font=("times new roman",15,"bold"))
        DataFrameLeft.place(x=0,y=5,width=900,height=360)

        label_member=Label(DataFrameLeft,text="Member Type",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_member.grid(row=0,column=0,sticky=W)

        comMember=ttk.Combobox(DataFrameLeft,textvariable=self.member_var,font=("arial",12,"bold"),width=27,state="readonly")
        comMember["value"]=("Admin Staff","Student","Lecturer")
        comMember.current(0)
        comMember.grid(row=0,column=1)

        label_PRN=Label(DataFrameLeft,text="PRN No.:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_PRN.grid(row=1,column=0,sticky=W)
        txt_PRN=Entry(DataFrameLeft,textvariable=self.prn_var,font=("arial",12,"bold"),width=29)
        txt_PRN.grid(row=1,column=1)

        label_ID=Label(DataFrameLeft,text="Registration No.:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_ID.grid(row=2,column=0,sticky=W)
        txt_ID=Entry(DataFrameLeft,textvariable=self.id_var,font=("arial",12,"bold"),width=29)
        txt_ID.grid(row=2,column=1)

        label_FirstName=Label(DataFrameLeft,text="First Name:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_FirstName.grid(row=3,column=0,sticky=W)
        txt_FirstName=Entry(DataFrameLeft,textvariable=self.firstname_var,font=("arial",12,"bold"),width=29)
        txt_FirstName.grid(row=3,column=1)

        label_LastName=Label(DataFrameLeft,text="Last Name:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_LastName.grid(row=4,column=0,sticky=W)
        txt_LastName=Entry(DataFrameLeft,textvariable=self.lastname_var,font=("arial",12,"bold"),width=29)
        txt_LastName.grid(row=4,column=1)

        label_Year=Label(DataFrameLeft,text="Year:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_Year.grid(row=5,column=0,sticky=W)
        txt_Year=Entry(DataFrameLeft,textvariable=self.year_var,font=("arial",12,"bold"),width=29)
        txt_Year.grid(row=5,column=1)

        label_Branch=Label(DataFrameLeft,text="Branch:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_Branch.grid(row=6,column=0,sticky=W)
        txt_Branch=Entry(DataFrameLeft,textvariable=self.branch_var,font=("arial",12,"bold"),width=29)
        txt_Branch.grid(row=6,column=1)

        label_email=Label(DataFrameLeft,text="Email:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_email.grid(row=7,column=0,sticky=W)
        txt_email=Entry(DataFrameLeft,textvariable=self.email_var,font=("arial",12,"bold"),width=29)
        txt_email.grid(row=7,column=1)

        label_mobile=Label(DataFrameLeft,text="Mobile No.:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_mobile.grid(row=8,column=0,sticky=W)
        txt_mobile=Entry(DataFrameLeft,textvariable=self.mobile_var,font=("arial",12,"bold"),width=29)
        txt_mobile.grid(row=8,column=1)

        label_BookID=Label(DataFrameLeft,text="Book ID:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_BookID.grid(row=0,column=2,sticky=W)
        txt_BookID=Entry(DataFrameLeft,textvariable=self.bookid_var,font=("arial",12,"bold"),width=29)
        txt_BookID.grid(row=0,column=3)

        label_BookTitle=Label(DataFrameLeft,text="Book Title:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_BookTitle.grid(row=1,column=2,sticky=W)
        txt_BookTitle=Entry(DataFrameLeft,textvariable=self.booktitle_var,font=("arial",12,"bold"),width=29)
        txt_BookTitle.grid(row=1,column=3)

        label_Author=Label(DataFrameLeft,text="Author Name:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_Author.grid(row=2,column=2,sticky=W)
        txt_Author=Entry(DataFrameLeft,textvariable=self.author_var,font=("arial",12,"bold"),width=29)
        txt_Author.grid(row=2,column=3)

        label_DateBorrowed=Label(DataFrameLeft,text="Date Borrowed:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_DateBorrowed.grid(row=3,column=2,sticky=W)
        txt_DateBorrowed=Entry(DataFrameLeft,textvariable=self.dateborrowed_var,font=("arial",12,"bold"),width=29)
        txt_DateBorrowed.grid(row=3,column=3)

        label_Due=Label(DataFrameLeft,text="Date Due:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_Due.grid(row=4,column=2,sticky=W)
        txt_Due=Entry(DataFrameLeft,textvariable=self.datedue_var,font=("arial",12,"bold"),width=29)
        txt_Due.grid(row=4,column=3)

        label_DaysOnBook=Label(DataFrameLeft,text="Days of Books:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_DaysOnBook.grid(row=5,column=2,sticky=W)
        txt_DaysOnBook=Entry(DataFrameLeft,textvariable=self.daysofbook_var,font=("arial",12,"bold"),width=29)
        txt_DaysOnBook.grid(row=5,column=3)

        label_LateReturnFine=Label(DataFrameLeft,text="Late Return Fine:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_LateReturnFine.grid(row=6,column=2,sticky=W)
        txt_LateReturnFine=Entry(DataFrameLeft,textvariable=self.latereturnfine_var,font=("arial",12,"bold"),width=29)
        txt_LateReturnFine.grid(row=6,column=3)

        label_DateOverdue=Label(DataFrameLeft,text="Date Over Due:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_DateOverdue.grid(row=7,column=2,sticky=W)
        txt_DateOverdue=Entry(DataFrameLeft,textvariable=self.dateoverdue_var,font=("arial",12,"bold"),width=29)
        txt_DateOverdue.grid(row=7,column=3)

        label_ActualPrice=Label(DataFrameLeft,text="Actual Price:",bg="SteelBlue2",font=("arial",12,"bold"),padx=2,pady=6)
        label_ActualPrice.grid(row=8,column=2,sticky=W)
        txt_ActualPrice=Entry(DataFrameLeft,textvariable=self.finalprice_var,font=("arial",12,"bold"),width=29)
        txt_ActualPrice.grid(row=8,column=3)

        #============ DataFrameRight ==============

        DataFrameRight=LabelFrame(frame,text="Book Details",bg="SteelBlue2",fg="RoyalBlue4",bd=12,relief=RIDGE,font=("times new roman",15,"bold"))
        DataFrameRight.place(x=910,y=5,width=560,height=360)

        self.txtBox=Text(DataFrameRight,font=("arial",12,"bold"),width=32,height=16,padx=2,pady=6)
        self.txtBox.grid(row=0,column=2)

        listScrollBar=Scrollbar(DataFrameRight)
        listScrollBar.grid(row=0,column=1,sticky="ns")
        
        listBooks=['Head First Book','Learn Python The Hard Way','Python Programming','Secrete Rahshy','Python CookBook','Into the Machine Learning','Fluent Python','Programming Python','The Algorithm','The Technic Python','Machine Tecno','My Python','Joss Elifff Guru','Elite jungle python','Just python','Basic Python','Advanced python','Data science with python','Machine learning with python','AI/ML with python','Data Analysis using python','Data Visualization using python']
        
        def SelectBook(event=""):
            value=str(listBox.get(listBox.curselection()))
            x=value
            if(x=="Head First Book"):
                self.bookid_var.set("BKID4665")
                self.booktitle_var.set("Head First Book")
                self.author_var.set("Paul berry")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹789")

            elif(x=="Learn Python The Hard Way"):
                self.bookid_var.set("BKID4625")
                self.booktitle_var.set("Learn Python The Hard Way")
                self.author_var.set("Nasaberry")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹489")

            elif(x=="Python Programming"):
                self.bookid_var.set("BKID4165")
                self.booktitle_var.set("Python Programming")
                self.author_var.set("Saanp")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹781")

            elif(x=="Secrete Rahshy"):
                self.bookid_var.set("BKID4235")
                self.booktitle_var.set("Secrete Rahshy")
                self.author_var.set("JK Rowling")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹20")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹234")

            elif(x=="Python CookBook"):
                self.bookid_var.set("BKID4125")
                self.booktitle_var.set("Python CookBook")
                self.author_var.set("Alaistair Cook")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹840")

            elif(x=="Into the Machine Learning"):
                self.bookid_var.set("BKID4345")
                self.booktitle_var.set("Into the Machine Learning")
                self.author_var.set("Prof. Vaishali Ingale")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹30")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹562")

            elif(x=="Fluent Python"):
                self.bookid_var.set("BKID4115")
                self.booktitle_var.set("Fluent Python")
                self.author_var.set("Fraz")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹720")

            if(x=="Programming Python"):
                self.bookid_var.set("BKID4333")
                self.booktitle_var.set("Programming Python")
                self.author_var.set("Catick")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹811")

            elif(x=="The Algorithm"):
                self.bookid_var.set("BKID5111")
                self.booktitle_var.set("The Algorithm")
                self.author_var.set("RohitRKS")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹1089")

            elif(x=="The Technic Python"):
                self.bookid_var.set("BKID4362")
                self.booktitle_var.set("The Technic Python")
                self.author_var.set("Tech Burner")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹480")

            elif(x=="Machine Tecno"):
                self.bookid_var.set("BKID4995")
                self.booktitle_var.set("Machine Tecno")
                self.author_var.set("Mechanix")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹700")

            elif(x=="My Python"):
                self.bookid_var.set("BKID4789")
                self.booktitle_var.set("My Python")
                self.author_var.set("Pysnaker")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹799")

            elif(x=="Joss Elifff Guru"):
                self.bookid_var.set("BKID5656")
                self.booktitle_var.set("Joss Elifff Guru")
                self.author_var.set("Joss Eliff")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹699")

            elif(x=="Elite jungle python"):
                self.bookid_var.set("BKID4444")
                self.booktitle_var.set("Elite jungle python")
                self.author_var.set("Josh Inglis")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹599")

            elif(x=="Just python"):
                self.bookid_var.set("BKID5555")
                self.booktitle_var.set("Just python")
                self.author_var.set("Praveen")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹899")

            elif(x=="Basic Python"):
                self.bookid_var.set("BKID6665")
                self.booktitle_var.set("Basic Python")
                self.author_var.set("Shivank")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹689")

            elif(x=="Advanced python"):
                self.bookid_var.set("BKID4990")
                self.booktitle_var.set("Advanced python")
                self.author_var.set("Aditi icche")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹899")

            elif(x=="Data science with python"):
                self.bookid_var.set("BKID4111")
                self.booktitle_var.set("Data science with python")
                self.author_var.set("Dr. Rupali Bagate")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹909")

            elif(x=="Machine learning with python"):
                self.bookid_var.set("BKID4333")
                self.booktitle_var.set("Machine learning with python")
                self.author_var.set("Lokii")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹749")

            elif(x=="AI/ML with python"):
                self.bookid_var.set("BKID6666")
                self.booktitle_var.set("AI/ML with python")
                self.author_var.set("Prabhat")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹1099")

            elif(x=="Data Analysis using python"):
                self.bookid_var.set("BKID6641")
                self.booktitle_var.set("Data Analysis using python")
                self.author_var.set("Majdur")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹999")

            elif(x=="Data Visualization using python"):
                self.bookid_var.set("BKID6969")
                self.booktitle_var.set("Data Visualization using python")
                self.author_var.set("Parii")

                d1=datetime.date.today()
                d2=datetime.timedelta(days=15)
                d3=d1+d2
                self.dateborrowed_var.set(d1)
                self.datedue_var.set(d3)
                self.daysofbook_var.set(15)
                self.latereturnfine_var.set("₹50")
                self.dateoverdue_var.set("NO")
                self.finalprice_var.set("₹1249")


        listBox=Listbox(DataFrameRight,font=("arial",12,"bold"),width=20,height=16)
        listBox.bind("<<ListboxSelect>>",SelectBook)
        listBox.grid(row=0,column=0,padx=4)
        listScrollBar.config(command=listBox.yview)

        for item in listBooks:
            listBox.insert(END,item)

        #============ Buttons Frame ==============

        ButtonFrame=Frame(self.root,bd=12,relief=RIDGE,padx=35,bg="deep sky blue")
        ButtonFrame.place(x=0,y=530,width=1536,height=70)

        btn_AddData=Button(ButtonFrame,command=self.add_data,text="Add Data",font=("arial",12,"bold"),width=23,bg="blue4",fg="white")
        btn_AddData.grid(row=0,column=0)

        btn_ShowData=Button(ButtonFrame,command=self.showData,text="Show Data",font=("arial",12,"bold"),width=23,bg="blue4",fg="white")
        btn_ShowData.grid(row=0,column=1)

        btn_Update=Button(ButtonFrame,command=self.updateData,text="Update",font=("arial",12,"bold"),width=23,bg="blue4",fg="white")
        btn_Update.grid(row=0,column=2)

        btn_Delete=Button(ButtonFrame,command=self.deleteData,text="Delete",font=("arial",12,"bold"),width=23,bg="blue4",fg="white")
        btn_Delete.grid(row=0,column=3)

        btn_Reset=Button(ButtonFrame,command=self.reset,text="Reset",font=("arial",12,"bold"),width=23,bg="blue4",fg="white")
        btn_Reset.grid(row=0,column=4)

        btn_Exit=Button(ButtonFrame,command=self.iExit,text="Exit",font=("arial",12,"bold"),width=23,bg="blue4",fg="white")
        btn_Exit.grid(row=0,column=5)

        #============ Information Frame ==============

        DetailsFrame=Frame(self.root,bd=12,relief=RIDGE,padx=20,bg="light sky blue")
        DetailsFrame.place(x=0,y=600,width=1536,height=195)

        table_frame=Frame(DetailsFrame,bd=6,relief=RIDGE,bg="light sky blue")
        table_frame.place(x=0,y=2,width=1470,height=190)

        xscroll=ttk.Scrollbar(table_frame,orient=HORIZONTAL)
        yscroll=ttk.Scrollbar(table_frame,orient=VERTICAL)

        self.library_table=ttk.Treeview(table_frame,column=("membertype","prnno","title","firstname","lastname","year","branch",
                                                            "email","mobile","bookid","booktitle","author","dateborrowed","datedue",
                                                            "days","latereturnfine","dateoverdue","finalprice"),xscrollcommand=xscroll.set,
                                                            yscrollcommand=yscroll.set)
        
        xscroll.pack(side=BOTTOM,fill=X)
        yscroll.pack(side=RIGHT,fill=Y)

        xscroll.config(command=self.library_table.xview)
        yscroll.config(command=self.library_table.yview)
        
        self.library_table.heading("membertype",text="Member Type")
        self.library_table.heading("prnno",text="PRN No.")
        self.library_table.heading("title",text="Registration No.")
        self.library_table.heading("firstname",text="First Name")
        self.library_table.heading("lastname",text="Last Name")
        self.library_table.heading("year",text="Year")
        self.library_table.heading("branch",text="Branch")
        self.library_table.heading("email",text="E-mail")
        self.library_table.heading("mobile",text="Mobile No.")
        self.library_table.heading("bookid",text="Book ID")
        self.library_table.heading("booktitle",text="Book Title")
        self.library_table.heading("author",text="Author")
        self.library_table.heading("dateborrowed",text="Date of Borrow")
        self.library_table.heading("datedue",text="Due Date")
        self.library_table.heading("days",text="Days On Book")
        self.library_table.heading("latereturnfine",text="Late Return Fine")
        self.library_table.heading("dateoverdue",text="Date Overdue")
        self.library_table.heading("finalprice",text="Final Price")

        self.library_table["show"]="headings"
        self.library_table.pack(fill=BOTH,expand=1)

        self.library_table.column("membertype",width=100)
        self.library_table.column("prnno",width=100)
        self.library_table.column("title",width=100)
        self.library_table.column("firstname",width=100)
        self.library_table.column("lastname",width=100)
        self.library_table.column("year",width=100)
        self.library_table.column("branch",width=100)
        self.library_table.column("email",width=240)
        self.library_table.column("mobile",width=120)
        self.library_table.column("bookid",width=100)
        self.library_table.column("booktitle",width=100)
        self.library_table.column("author",width=100)
        self.library_table.column("dateborrowed",width=100)
        self.library_table.column("datedue",width=100)
        self.library_table.column("days",width=100)
        self.library_table.column("latereturnfine",width=100)
        self.library_table.column("dateoverdue",width=100)
        self.library_table.column("finalprice",width=100)

        self.fetch_data()
        self.library_table.bind("<ButtonRelease-1>",self.get_cursor)
        

    def add_data(self):
        conn=mysql.connector.connect(host="localhost",username="root",password="root",database="mydata")
        my_cursor=conn.cursor()
        my_cursor.execute("insert into library values(%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s)",(
                                                                                                                self.member_var.get(),
                                                                                                                self.prn_var.get(),
                                                                                                                self.id_var.get(),
                                                                                                                self.firstname_var.get(),
                                                                                                                self.lastname_var.get(),
                                                                                                                self.year_var.get(),
                                                                                                                self.branch_var.get(),
                                                                                                                self.email_var.get(),
                                                                                                                self.mobile_var.get(),
                                                                                                                self.bookid_var.get(),
                                                                                                                self.booktitle_var.get(),
                                                                                                                self.author_var.get(),
                                                                                                                self.dateborrowed_var.get(),
                                                                                                                self.datedue_var.get(),
                                                                                                                self.daysofbook_var.get(),
                                                                                                                self.latereturnfine_var.get(),
                                                                                                                self.dateoverdue_var.get(),
                                                                                                                self.finalprice_var.get()
                                                                                                              ))
        conn.commit()
        self.fetch_data()
        conn.close()

        messagebox.showinfo("Success","Member details has been added successfully.")

    def updateData(self):
        conn=mysql.connector.connect(host="localhost",username="root",password="root",database="mydata")
        my_cursor=conn.cursor()
        my_cursor.execute("update library set Member=%s,ID=%s,FirstName=%s,LastName=%s,Year=%s,Branch=%s,Email=%s,Mobile=%s,BookID=%s,BookTitle=%s,Author=%s,DateBorrowed=%s,DateDue=%s,daysofbook=%s,LateReturnFine=%s,DateOverdue=%s,finalprice=%s where PRN_NO=%s",(
                                                                                                                                                                                                                                                                        self.member_var.get(),
                                                                                                                                                                                                                                                                        self.id_var.get(),
                                                                                                                                                                                                                                                                        self.firstname_var.get(),
                                                                                                                                                                                                                                                                        self.lastname_var.get(),
                                                                                                                                                                                                                                                                        self.year_var.get(),
                                                                                                                                                                                                                                                                        self.branch_var.get(),
                                                                                                                                                                                                                                                                        self.email_var.get(),
                                                                                                                                                                                                                                                                        self.mobile_var.get(),
                                                                                                                                                                                                                                                                        self.bookid_var.get(),
                                                                                                                                                                                                                                                                        self.booktitle_var.get(),
                                                                                                                                                                                                                                                                        self.author_var.get(),
                                                                                                                                                                                                                                                                        self.dateborrowed_var.get(),
                                                                                                                                                                                                                                                                        self.datedue_var.get(),
                                                                                                                                                                                                                                                                        self.daysofbook_var.get(),
                                                                                                                                                                                                                                                                        self.latereturnfine_var.get(),
                                                                                                                                                                                                                                                                        self.dateoverdue_var.get(),
                                                                                                                                                                                                                                                                        self.finalprice_var.get(),
                                                                                                                                                                                                                                                                        self.prn_var.get()                                                                                    
                                                                                                                                                                                                                                                                    ))
        conn.commit()
        self.fetch_data()
        self.reset()
        conn.close()

        messagebox.showinfo("Success","Member details has been updated successfully")

    def fetch_data(self):
        conn=mysql.connector.connect(host="localhost",username="root",password="root",database="mydata")
        my_cursor=conn.cursor()
        my_cursor.execute("select * from library")
        rows=my_cursor.fetchall()

        if len(rows)!=0:
            self.library_table.delete(*self.library_table.get_children())
            for i in rows:
                self.library_table.insert("",END,values=i)
            conn.commit()
        conn.close()

    def get_cursor(self,event=""):
        cursor_row=self.library_table.focus()
        content=self.library_table.item(cursor_row)
        row=content['values']

        self.member_var.set(row[0]),
        self.prn_var.set(row[1]),
        self.id_var.set(row[2]),
        self.firstname_var.set(row[3]),
        self.lastname_var.set(row[4]),
        self.year_var.set(row[5]),
        self.branch_var.set(row[6]),
        self.email_var.set(row[7]),
        self.mobile_var.set(row[8]),
        self.bookid_var.set(row[9]),
        self.booktitle_var.set(row[10]),
        self.author_var.set(row[11]),
        self.dateborrowed_var.set(row[12]),
        self.datedue_var.set(row[13]),
        self.daysofbook_var.set(row[14]),
        self.latereturnfine_var.set(row[15]),
        self.dateoverdue_var.set(row[16]),
        self.finalprice_var.set(row[17])

    def showData(self):
        self.txtBox.insert(END,"Member Type:\t\t"+self.member_var.get()+"\n")
        self.txtBox.insert(END,"PRN No.:\t\t"+self.prn_var.get() +"\n")
        self.txtBox.insert(END,"Registration No.:\t\t"+self.id_var.get() +"\n")
        self.txtBox.insert(END,"First Name:\t\t"+self.firstname_var.get() +"\n")
        self.txtBox.insert(END,"Last Name:\t\t"+self.lastname_var.get() +"\n")
        self.txtBox.insert(END,"Year:\t\t"+self.year_var.get() +"\n")
        self.txtBox.insert(END,"Branch:\t\t"+self.branch_var.get() +"\n")
        self.txtBox.insert(END,"E-mail:\t\t"+self.email_var.get() +"\n")
        self.txtBox.insert(END,"Mobile No.:\t\t"+self.mobile_var.get() +"\n")
        self.txtBox.insert(END,"Book ID:\t\t"+self.bookid_var.get() +"\n")
        self.txtBox.insert(END,"Book Title:\t\t"+self.booktitle_var.get() +"\n")
        self.txtBox.insert(END,"Author:\t\t"+self.author_var.get() +"\n")
        self.txtBox.insert(END,"Date Borrowed:\t\t"+self.dateborrowed_var.get() +"\n")
        self.txtBox.insert(END,"Date Due:\t\t"+self.datedue_var.get() +"\n")
        self.txtBox.insert(END,"Days of Book:\t\t"+self.daysofbook_var.get() +"\n")
        self.txtBox.insert(END,"Late Return Fine:\t\t"+self.latereturnfine_var.get() +"\n")
        self.txtBox.insert(END,"Date Overdue:\t\t"+self.dateoverdue_var.get() +"\n")
        self.txtBox.insert(END,"Final Price:\t\t"+self.finalprice_var.get() +"\n")

    def reset(self):
        self.member_var.set("")
        self.prn_var.set("")
        self.id_var.set("")
        self.firstname_var.set("")
        self.lastname_var.set("")
        self.year_var.set("")
        self.branch_var.set("")
        self.email_var.set("")
        self.mobile_var.set("")
        self.bookid_var.set("")
        self.booktitle_var.set("")
        self.author_var.set("")
        self.dateborrowed_var.set("")
        self.datedue_var.set("")
        self.daysofbook_var.set("")
        self.latereturnfine_var.set("")
        self.dateoverdue_var.set("")
        self.finalprice_var.set("")
        self.txtBox.delete("1.0",END)

    def iExit(self):
        iExit=tkinter.messagebox.askyesno("Library Management System","Do you want to exit")
        if iExit>0:
            self.root.destroy()
            return
        
    def deleteData(self):
        if self.prn_var.get()=="" or self.id_var.get()=="":
            messagebox.showerror("Error","First Select the Member")
        else:
            conn=mysql.connector.connect(host="localhost",username="root",password="root",database="mydata")
            my_cursor=conn.cursor()
            query="delete from library where PRN_NO=%s"
            value=(self.prn_var.get(),)
            my_cursor.execute(query,value)

            conn.commit()
            self.fetch_data()
            self.reset()
            conn.close()

            messagebox.showinfo("Success","Member has been deleted successfully")


if __name__=="__main__":
    root=Tk()
    obj=LibraryManagementSystem(root)
    root.mainloop()
