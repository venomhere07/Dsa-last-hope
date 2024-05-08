#include <iostream>
using namespace std;

class Node
{
    string name;
    Node *down;
    Node *next;
    int flag;

public:
    Node()
    {
        down = NULL;
        next = NULL;
        flag = 0;
    }
    Node(string name)
    {
        this->name = name;
        down = NULL;
        next = NULL;
        flag = 0;
    }
    void createbook(Node *&);
    void insertc(Node *&);
    void inserts(Node *&);
    void insertss(Node *&);
    void displayb(Node *&);
};

void Node::createbook(Node *&head)
{
    if (head == NULL)
    {
        cout << "Enter book name" << endl;
        string bookname;
        cin >> bookname;
        Node *temp = new Node(bookname);
        head = temp;
    }
    else
    {
        cout << "Book already exits" << endl;
    }
}

void Node::insertc(Node *&head)
{
    if (head == NULL)
    {
        cout << "Book do not Exits";
    }
    else if (head->down == NULL)
    {
        cout << "Enter chapter name" << endl;
        string chapname;
        cin >> chapname;
        Node *temp = new Node(chapname);
        head->down = temp;
        head->flag = 1;
    }
    else
    {
        Node *temp = head->down;
        while (temp->next != NULL)
        {
            temp = temp->next;
        }
        cout << "Enter chapter name" << endl;
        string chapname;
        cin >> chapname;
        Node *chapter = new Node(chapname);
        temp->next = chapter;
    }
}

void Node::inserts(Node *&head)
{
    if (head == NULL)
    {
        cout << "Book is not exit" << endl;
    }
    else
    {
        Node *temp = head->down;
        if (temp == NULL)
        {
            cout << "No chapter in this book exits" << endl;
        }
        else
        {
            string chaptername;
            cout << "Enter chapter for which you want to insert section" << endl;
            cin >> chaptername;
            while (temp != NULL)
            {
                if (temp->name == chaptername)
					{
						break;
					}
                temp = temp->next;
            }
            if (temp == NULL)
            {
                cout << "No such chapter name is found" << endl;
            }
            else
            {
                string secname;
                cout << "Enter section for " << temp->name << " :" << endl;
                cin >> secname;
                Node *temp2 = new Node(secname);
                if (temp->down == NULL)
                {
                    temp->down = temp2;
                }
                else
                {
                    Node *temp3 = temp->down;
                    while (temp3->next != NULL)
                    {
                        temp3 = temp3->next;
                    }
                    temp3->next = temp2;
                }
            }
        }
    }
}


void Node::insertss(Node *&head)
{
    if (head == NULL)
    {
        cout << "Book is not exit" << endl;
    }
    else
    {
        Node *temp = head->down;
        if (temp == NULL)
        {
            cout << "No chapter in this book exits" << endl;
        }
        else
        {
            string chaptername;
            cout << "Enter chapter for which you want to insert section" << endl;
            cin >> chaptername;
            while (temp != NULL)
            {
                if (temp->name == chaptername)
                {
                    break;
                }
                temp = temp->next;
            }
            if (temp == NULL)
            {
                cout << "No such chapter name is found" << endl;
            }
            else
            {
                string sectionname;
                cout << "Enter sectionname for "<<temp->name<<endl;
                cin >> sectionname;
                Node* temp1=temp->down;
                while (temp1!=NULL)
                {
                    if(temp1->name==sectionname){
                        break;
                    }
                    temp1=temp1->next;
                }
                


                string subsecname;
                cout << "Enter subsection for " << temp1->name << " :" << endl;
                cin >> subsecname;
                Node *temp2 = new Node(subsecname);
                if (temp1->down == NULL)
                {
                    temp1->down = temp2;
                }
                else
                {
                    Node *temp3 = temp1->down;
                    while (temp3->next != NULL)
                    {
                        temp3 = temp3->next;
                    }
                    temp3->next = temp2;
                }
            }
        }
    }
}
void Node::displayb(Node *&head)
{
    if (head == NULL)
    {
        cout << "No book is available" << endl;
    }
    else
    {
        cout << "Book Name is :" << head->name << endl;
        Node *temp = head->down;
        while (temp != NULL)
        {
            cout << "chapter are :" << temp->name << endl;
            Node *temp1 = temp->down;
            while (temp1 != NULL)
            {
                cout << "section are :" << temp1->name << endl;
                Node *temp2 = temp1->down;
                while (temp2 != NULL)
                {
                    cout << "Subsection are :" << temp2->name << endl;
                    temp2 = temp2->next;
                }
                temp1 = temp1->next;
            }
            temp = temp->next;
        }
    }
}
int main()
{
    Node *head = NULL;
    Node obj;
    int n = 0;
    while (n != 6)
    {
        cout << "Enter 1 for creation of book" << endl;
        cout << "Enter 2 for insertb of chapter" << endl;
        cout << "Enter 2 for insertion of section" << endl;
        cout << "Enter 4 for insertion of subsection" << endl;
        cout << "Enter 5 for display" << endl;
        cout << "Enter 6 for exit from loop" << endl;
        cin >> n;
        switch (n)
        {
        case 1:
            obj.createbook(head);
            break;
        case 2:
            obj.insertc(head);
            break;
        case 3:
            obj.inserts(head);
            break;
        case 4:
            obj.insertss(head);
            break;
        case 5:
            obj.displayb(head);
            break;
        default:
            cout << "you are not enter the valid option" << endl;
            break;
        }
    }
    return 0;
}