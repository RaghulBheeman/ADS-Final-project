#include<iostream>
#include <vector>
#include <list>
#include <iterator>
using namespace std;
class Edge;
class Vertex;
class Edge {
 public:
 int DestinationVertexID;
 int weight;
 Edge() {}
 Edge(int destVID, int w) {
 DestinationVertexID = destVID;
 weight = w;
 }
 void setEdgeValues(int destVID, int w) {
 DestinationVertexID = destVID;
 weight = w;
 }
 void setWeight(int w) {
 weight = w;
 }
 int getDestinationVertexID() {
 return DestinationVertexID;
 }
 int getWeight() {
 return weight;
 }
};
class Vertex {
 public:
 int course_id;
 string course_name;
 list < Edge > edgeList;
 Vertex() {
 course_id = 0;
 course_name = "";
 }
 Vertex(int id, string cname) {
 course_id = id;
 course_name = cname;
 }
 int getCourseID() {
 return course_id;
 }
 string getCourseName() {
 return course_name;
 }
 void setID(int id) {
 course_id = id;
 }
 void setCourseName(string cname) {
 course_name = cname;
 }
 //void add_course(string cname,int id1){
 //string courses[id1]=cname;
 //for(int i=0;i<id1;i++){
 // cout<<courses[i];
 //}
 //return courses[id1];
 //cout<< courses;
 //}
 list < Edge > getEdgeList() {
 return edgeList;
 }
 // void addEdgeToEdgelist(int toVertexID, int weight)
 // {
 // Edge e(toVertexID,weight);
 // edgeList.push_back(e); 
 // cout<<"Edge between "<<course_id<<" and "<<toVertexID<<" added Successfully"<<endl; 
 // }
 void printEdgeList() {
 cout << "[";
 for (auto it = edgeList.begin(); it != edgeList.end(); it++) {
 cout << it -> getDestinationVertexID() << "(" << it -> getWeight() << ") --> ";
 }
 cout << "]";
 cout << endl;
 }
 void updateVertexName(string cname) {
 course_name = cname;
 cout << "Course Name Updated Successfully";
 }
};
class Graph {
 vector < Vertex > vertices;
 public:
 bool checkIfVertexExistByID(int vid) {
 bool flag = false;
 for (int i = 0; i < vertices.size(); i++) {
 if (vertices.at(i).getCourseID() == vid) {
 return true;
 }
 }
 return flag;
 }
 void addVertex(Vertex newVertex) {
 bool check = checkIfVertexExistByID(newVertex.getCourseID());
 if (check == true) {
 cout << "Course with this ID already exist" << endl;
 } else {
 vertices.push_back(newVertex);
 cout << "New Course Added Successfully" << endl;
 }
 }
 Vertex getVertexByID(int vid) {
 Vertex temp;
 for (int i = 0; i < vertices.size(); i++) {
 temp = vertices.at(i);
 if (temp.getCourseID() == vid) {
 return temp;
 }
 }
 return temp;
 }
 bool checkIfEdgeExistByID(int fromVertex, int toVertex) {
 Vertex v = getVertexByID(fromVertex);
 list < Edge > e;
 e = v.getEdgeList();
 bool flag = false;
 for (auto it = e.begin(); it != e.end(); it++) {
 if (it -> getDestinationVertexID() == toVertex) {
 flag = true;
 return flag;
 break;
 }
 }
 return flag;
 }
 void updateVertex(int oldVID, string vname) {
 bool check = checkIfVertexExistByID(oldVID);
 if (check == true) {
 for (int i = 0; i < vertices.size(); i++) {
 if (vertices.at(i).getCourseID() == oldVID) {
 vertices.at(i).setCourseName(vname);
 break;
 }
 }
 cout << " course Updated Successfully " << endl;
 }
 }
 void addEdgeByID(int fromVertex, int toVertex, int weight) {
 bool check1 = checkIfVertexExistByID(fromVertex);
 bool check2 = checkIfVertexExistByID(toVertex);
 bool check3 = checkIfEdgeExistByID(fromVertex, toVertex);
 if ((check1 && check2 == true)) {
 if (check3 == true) {
 cout << "Bridge between " << getVertexByID(fromVertex).getCourseName() << "(" << fromVertex << ") and " << 
getVertexByID(toVertex).getCourseName() << "(" << toVertex << ") Already Exist" << endl;
 } else {
 for (int i = 0; i < vertices.size(); i++) {
 if (vertices.at(i).getCourseID() == fromVertex) {
 Edge e(toVertex, weight);
 //edgeList.push_back(e); 
 //vertices.at(i).addEdgeToEdgelist(toVertex,weight);
 vertices.at(i).edgeList.push_back(e);
 } else if (vertices.at(i).getCourseID() == toVertex) {
 Edge e(toVertex, weight);
 //edgeList.push_back(e); 
 //vertices.at(i).addEdgeToEdgelist(fromVertex,weight);
 vertices.at(i).edgeList.push_back(e);
 }
 }
 cout << "Bridge mark between " << fromVertex << " and " << toVertex << " added Successfully" << endl;
 }
 } else {
 cout << "Invalid course ID entered.";
 }
 }
 void updateEdgeByID(int fromVertex, int toVertex, int newWeight) {
 bool check = checkIfEdgeExistByID(fromVertex, toVertex);
 if (check == true) {
 for (int i = 0; i < vertices.size(); i++) {
 if (vertices.at(i).getCourseID() == fromVertex) {
 for (auto it = vertices.at(i).edgeList.begin(); it != vertices.at(i).edgeList.end(); it++) {
 if (it -> getDestinationVertexID() == toVertex) {
 it -> setWeight(newWeight);
 break;
 }
 }
 } else if (vertices.at(i).getCourseID() == toVertex) {
 for (auto it = vertices.at(i).edgeList.begin(); it != vertices.at(i).edgeList.end(); it++) {
 if (it -> getDestinationVertexID() == fromVertex) {
 it -> setWeight(newWeight);
 break;
 }
 }
 }
 }
 cout << "Bridge mark Updated Successfully " << endl;
 } else {
 cout << "Bridge between " << getVertexByID(fromVertex).getCourseName() << "(" << fromVertex << ") and " << 
getVertexByID(toVertex).getCourseName() << "(" << toVertex << ") DOES NOT Exist" << endl;
 }
 }
 void deleteEdgeByID(int fromVertex, int toVertex) {
 bool check = checkIfEdgeExistByID(fromVertex, toVertex);
 if (check == true) {
 for (int i = 0; i < vertices.size(); i++) {
 if (vertices.at(i).getCourseID() == fromVertex) {
 for (auto it = vertices.at(i).edgeList.begin(); it != vertices.at(i).edgeList.end(); it++) {
 if (it -> getDestinationVertexID() == toVertex) {
 vertices.at(i).edgeList.erase(it);
 //cout<<"First erase"<<endl;
 break;
 }
 }
 }
 if (vertices.at(i).getCourseID() == toVertex) {
 for (auto it = vertices.at(i).edgeList.begin(); it != vertices.at(i).edgeList.end(); it++) {
 if (it -> getDestinationVertexID() == fromVertex) {
 vertices.at(i).edgeList.erase(it);
 //cout<<"second erase"<<endl;
 break;
 }
 }
 }
 }
 cout << "Bridge Between " << fromVertex << " and " << toVertex << " Deleted Successfully." << endl;
 }
 }
 void deleteVertexByID(int vid) {
 int vIndex = 0;
 for (int i = 0; i < vertices.size(); i++) {
 if (vertices.at(i).getCourseID() == vid) {
 vIndex = i;
 }
 }
 for (int i = 0; i < vertices.size(); i++) {
 for (auto it = vertices.at(i).edgeList.begin(); it != vertices.at(i).edgeList.end(); it++) {
 if (it -> getDestinationVertexID() == vid) {
 vertices.at(i).edgeList.erase(it);
 break;
 }
 }
 }
 vertices.erase(vertices.begin() + vIndex);
 cout << "Course Deleted Successfully" << endl;
 }
 void getAllNeigborsByID(int vid) {
 cout << getVertexByID(vid).getCourseName() << " (" << getVertexByID(vid).getCourseID() << ") --> ";
 for (int i = 0; i < vertices.size(); i++) {
 if (vertices.at(i).getCourseID() == vid) {
 cout << "[";
 for (auto it = vertices.at(i).edgeList.begin(); it != vertices.at(i).edgeList.end(); it++) {
 cout << it -> getDestinationVertexID() << "(" << it -> getWeight() << ") --> ";
 }
 cout << "]";
 }
 }
 }
 void printGraph() {
 for (int i = 0; i < vertices.size(); i++) {
 Vertex temp;
 temp = vertices.at(i);
 cout << temp.getCourseName() << " (" << temp.getCourseID() << ") --> ";
 temp.printEdgeList();
 }
 }
};
void display(){
int n;
cout<< "Press 1 for basic courses"<<endl;
cout<< "Press 2 for intermediate courses"<<endl;
 cout<< "Press 3 for advanced courses"<<endl;
 cin>>n;
 cout<<endl;
 if(n==1){
 string courses[3]={"PL","PROBABILITY","HTML"};
 for(int i=0;i<3;i++){
 cout<<courses[i]<<endl;
 }
 cout<<endl;
 }
 if (n==2){
 string courses[3]={"DS","INFORMATION THEORY","CSS"};
 for(int i=0;i<3;i++){
 cout<<courses[i]<<endl;
 }
 cout<<endl;
 }
 if (n==3){
string courses[3]={"ADS","MACHINE LEARNING","WEB DESIGNING"};
for(int i=0;i<3;i++){
cout<<courses[i]<<endl;
}
cout<<endl;
}
}
bool signup(){
//int regs[10]=(reg);
cout<<"----->Signup<-----"<<endl;
for(int i=0;i<5;i++){
cout<<"Enter your register number"<<endl;
int reg;
cin>>reg;
cout<<"Enter your name"<<endl;
string name;
cin>>name;
cout<<"profile created successfully"<<endl;
cout<<"your password is "<<121+i<<endl;
break;
}
}
bool log_check(int password){
int passwords[10]={121,120,122,123,124,124,125,126,127,128};
for(int i=0;i<10;i++){
if(password==passwords[i]){
return true;
}
else{
return false;
}
}
}
int main() {
 Graph g;
 string cname;
 int id1, id2, w;
 int option;
 bool check;
 int mark;
 int login;
 string coursess;
cout<<"Press '1 for student login' or 'press 0 for admin login' "<<endl;
cin>>login;
if (login==true){
cout<<"------>WELCOME<------"<<endl;
cout<<"Press 1 for login or press 0 for signin"<<endl;
bool n;
cin>>n;
if (n==false){
//cout<<"Enter your name"<<endl;
//string name;
//cin>>name;
//cout<<"enter your reg no"<<endl;
//int reg;
//cin>>reg;
signup();
cout<<endl;
}
if(n=true){
cout<<"----->LOG IN<-----"<<endl;
cout<<"Enter your regno"<<endl;
int num;
cin>>num;
cout<<"enter your password"<<endl;
int password;
cin>>password;
if(log_check(password)==true){
 do {
 cout << "What operation do you want to perform? " <<
 " Select Option number. Enter 0 to exit." << endl;
 cout << "1. Check if 2 courses are linked" << endl;
 cout << "2. Print All linked courses of a course" << endl;
 cout << "3. Next level"<<endl;
 cout << "4.display courses"<<endl;
 cout << "5.login"<<endl;
 cout << "0. Exit Program" << endl;
 cin >> option;
 Vertex v1;
 switch (option) {
 case 0:
 break;
 
 case 1:
 cout << "Check if 2 courses are linked -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout << "courses are linked (Edge exist)";
 } else {
 cout << "courses are not linked (Edge does NOT exist)";
 }
 break;
 case 2:
 cout << "Print All linked course -" << endl;
 cout << "Enter ID of Course to fetch all linked courses : ";
 cin >> id1;
 g.getAllNeigborsByID(id1);
 break;
 
 case 3:
 cout << "Enter ID of your present course: ";
 cin >> id1;
 cout << "Enter ID of your next course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout<<"enter your mark"<<endl;
 cin>>mark;
 if(mark>=w){
 id1==id2;
 cout << "congratulations you are enrolled";
 }
 else if(mark<w){
 cout<<endl<<"your mark is low to do "<<cname<<endl;
 cout<<endl<<"you are not enrolled "<<endl;
 }
 else{
 cout<<"it is not allowed try related course";
 }
 }
 else {
 cout << endl<<"Prerequests not satisfied ,try some other related course "<<endl;
 }
 break;
 
case 4:
 cout<<"COURSES WE OFFER !"<<endl;
 display();
 break;
 
 case 5:
 cout<<"Press '1 for student login' or 'press 0 for admin login' "<<endl;
 cin>>login;
 if(login==false){
string password;
string keyword="SSN@123*";
cout<<"ENTER ADMIN PASSWORD:"<<endl;
cin>>password;
if (password==keyword){
 do {
 cout << "What operation do you want to perform? " <<
 " Select Option number. Enter 0 to exit." << endl;
 cout << "1. Add Course" << endl;
 cout << "2. Update Course" << endl;
 cout << "3. Delete Course" << endl;
 cout << "4. Add bridge marks" << endl;
 cout << "5. Update bridge marks" << endl;
 cout << "6. Delete bridge marks" << endl;
 cout << "7. Check if 2 courses are linked" << endl;
 cout << "8. Print All linked courses of a course" << endl;
 cout << "9. Next level"<<endl;
 cout << "10. Print Graph" << endl;
 cout << "11. Display courses"<<endl;
 cout << "12. login"<<endl;
 cout << "0. Exit Program" << endl;
 cin >> option;
 Vertex v1;
 switch (option) {
 case 0:
 break;
 case 1:
 cout << "Adding new course -" << endl;
 cout << "Enter Course ID :";
 cin >> id1;
 cout << "Enter Course Name :";
 cin >> cname;
 v1.setID(id1);
 v1.setCourseName(cname);
 g.addVertex(v1);
 //cout<<"Courses we offer"<<endl;
 //v1.add_course(cname,id1);
 break;
 case 2:
 cout << "Update course -" << endl;
 cout << "Enter course ID to update :";
 cin >> id1;
 cout << "Enter Course Name :";
 cin >> cname;
 g.updateVertex(id1, cname);
 break;
 case 3:
 cout << "Delete course -" << endl;
 cout << "Enter course ID to be deleted : ";
 cin >> id1;
 g.deleteVertexByID(id1);
 break;
 case 4:
 cout << "Add bridge mark -" << endl;
 cout << "Enter ID of source course: ";
 cin >> id1;
 cout << "Enter ID of destination Course: ";
 cin >> id2;
 if(id1>id2){
 cout<<"You are not allowed to bridge to lower courses";
 }
 else{
 
 cout << "Enter bridge mark: ";
 cin >> w;
 g.addEdgeByID(id1, id2, w);
 }
 break;
 case 5:
 cout << "Update bridge mark -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 cout << "Enter UPDATED bridge mark: ";
 cin >> w;
 g.updateEdgeByID(id1, id2, w);
 break;
 case 6:
 cout << "Delete bridge mark -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 g.deleteEdgeByID(id1, id2);
 break;
 case 7:
 cout << "Check if 2 courses are linked -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout << endl<<"courses are linked (Edge exist)"<<endl;
 } else {
 cout <<endl<< "courses are not linked (Edge does NOT exist)"<<endl;
 }
 break;
 case 8:
 cout <<"Print All linked course -" << endl;
 cout << "Enter ID of Course to fetch all linked courses : "<<endl;
 cin >> id1;
 g.getAllNeigborsByID(id1);
 break;
 
 case 9:
 cout << "Enter ID of your present course: ";
 cin >> id1;
 cout << "Enter ID of your next course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout<<"enter your mark"<<endl;
 cin>>mark;
 if(mark>=w){
 id1==id2;
 cout << "congratulations you are enrolled";
 }
 else if(mark<w){
 cout<<endl<<"your mark is low to do "<<cname<<endl;
 cout<<endl<<"you are not enrolled "<<endl;
 }
 else{
 cout<<"it is not allowed try related course";
 }
 }
 else {
 cout << endl<<"Prerequests not satisfied ,try some other related course "<<endl;
 }
 break;
 
 case 10:
 cout << "Print Graph Operation -" << endl;
 g.printGraph();
 break;
 
 case 11:
 cout<<"COURSES WE OFFER !"<<endl;
 display();
 
 break;
case 12:
cout<<"Press '1 for student login' or 'press 0 for admin login' "<<endl;
cin>>login;
if (login==true){
cout<<"------>WELCOME<------"<<endl;
cout<<"Press 1 for login or press 0 for signin"<<endl;
bool n;
cin>>n;
if (n==false){
//cout<<"Enter your name"<<endl;
//string name;
//cin>>name;
//cout<<"enter your reg no"<<endl;
//int reg;
//cin>>reg;
signup();
}
if(n=true){
cout<<endl<<"Enter your regno"<<endl;
int num;
cin>>num;
cout<<"enter your password"<<endl;
int password;
cin>>password;
if(log_check(password)==true){
do {
 cout << "What operation do you want to perform? " <<
 " Select Option number. Enter 0 to exit." << endl;
 cout << "1. Check if 2 courses are linked" << endl;
 cout << "2. Print All linked courses of a course" << endl;
 cout << "3. Next level"<<endl;
 cout << "4.display courses"<<endl;
 cout << "0. Exit Program" << endl;
 cin >> option;
 Vertex v1;
 switch (option) {
 case 0:
 break;
 
 case 1:
 cout << "Check if 2 courses are linked -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout << "courses are linked (Edge exist)";
 } else {
 cout << "courses are not linked (Edge does NOT exist)";
 }
 break;
 case 2:
 cout << "Print All linked course -" << endl;
 cout << "Enter ID of Course to fetch all linked courses : ";
 cin >> id1;
 g.getAllNeigborsByID(id1);
 break;
 
 case 3:
 cout << "Enter ID of your present course: ";
 cin >> id1;
 cout << "Enter ID of your next course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout<<"enter your mark"<<endl;
 cin>>mark;
 if(mark>=w){
 id1==id2;
 cout << "congratulations you are enrolled";
 }
 else if(mark<w){
 cout<<endl<<"your mark is low to do "<<cname<<endl;
 cout<<endl<<"you are not enrolled "<<endl;
 }
 else{
 cout<<"it is not allowed try related course";
 }
 }
 else {
 cout << endl<<"Prerequests not satisfied ,try some other related course "<<endl;
 }
 break;
 
case 4:
 cout<<"COURSES WE OFFER !"<<endl;
 display();
 break;
 
 default:
 cout << "Enter Proper Option number " << endl;
 }
 cout << endl;
 } while (option != 0);
}
 return 0;
}
 
default:
cout << "Enter Proper Option number " << endl;
 }
 // cout << endl;
}
 } while (option != 0);
}
//else{
//cout<<"Incorrect password"<<endl;
//}
}
return 0;
}
 
 
 
 
 
 //default:
 cout << "Enter Proper Option number " << endl;
 //}
 //cout << endl;
 } while (option != 0);
 return 0;
}
}
else{
cout<<"login failed"<<endl;
}
}
//else{
//cout<<"sign up first"<<endl;
//}
if(login==false){
string password;
string keyword="SSN@123*";
cout<<"ENTER ADMIN PASSWORD:"<<endl;
cin>>password;
if (password==keyword){
 do {
 cout << "What operation do you want to perform? " <<
 " Select Option number. Enter 0 to exit." << endl;
 cout << "1. Add Course" << endl;
 cout << "2. Update Course" << endl;
 cout << "3. Delete Course" << endl;
 cout << "4. Add bridge marks" << endl;
 cout << "5. Update bridge marks" << endl;
 cout << "6. Delete bridge marks" << endl;
 cout << "7. Check if 2 courses are linked" << endl;
 cout << "8. Print All linked courses of a course" << endl;
 cout << "9. Next level"<<endl;
 cout << "10. Print Graph" << endl;
 cout << "11. Display courses"<<endl;
 cout << "12. login"<<endl;
 cout << "0. Exit Program" << endl;
 cin >> option;
 Vertex v1;
 switch (option) {
 case 0:
 break;
 case 1:
 cout << "Adding new course -" << endl;
 cout << "Enter Course ID :";
 cin >> id1;
 cout << "Enter Course Name :";
 cin >> cname;
 v1.setID(id1);
 v1.setCourseName(cname);
 g.addVertex(v1);
 //cout<<"Courses we offer"<<endl;
 //v1.add_course(cname,id1);
 break;
 case 2:
 cout << "Update course -" << endl;
 cout << "Enter course ID to update :";
 cin >> id1;
 cout << "Enter Course Name :";
 cin >> cname;
 g.updateVertex(id1, cname);
 break;
 case 3:
 cout << "Delete course -" << endl;
 cout << "Enter course ID to be deleted : ";
 cin >> id1;
 g.deleteVertexByID(id1);
 break;
 case 4:
 cout << "Add bridge mark -" << endl;
 cout << "Enter ID of source course: ";
 cin >> id1;
 cout << "Enter ID of destination Course: ";
 cin >> id2;
 if(id1>id2){
 cout<<"You are not allowed to bridge to lower courses";
 }
 else{
 
 cout << "Enter bridge mark: ";
 cin >> w;
 g.addEdgeByID(id1, id2, w);
 }
 break;
 case 5:
 cout << "Update bridge mark -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 cout << "Enter UPDATED bridge mark: ";
 cin >> w;
 g.updateEdgeByID(id1, id2, w);
 break;
 case 6:
 cout << "Delete bridge mark -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 g.deleteEdgeByID(id1, id2);
 break;
 case 7:
 cout << "Check if 2 courses are linked -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout << endl<<"courses are linked (Edge exist)"<<endl;
 } else {
 cout <<endl<< "courses are not linked (Edge does NOT exist)"<<endl;
 }
 break;
 case 8:
 cout <<"Print All linked course -" << endl;
 cout << "Enter ID of Course to fetch all linked courses : "<<endl;
 cin >> id1;
 g.getAllNeigborsByID(id1);
 break;
 
 case 9:
 cout << "Enter ID of your present course: ";
 cin >> id1;
 cout << "Enter ID of your next course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout<<"enter your mark"<<endl;
 cin>>mark;
 if(mark>=w){
 id1==id2;
 cout << "congratulations you are enrolled";
 }
 else if(mark<w){
 cout<<endl<<"your mark is low to do "<<cname<<endl;
 cout<<endl<<"you are not enrolled "<<endl;
 }
 else{
 cout<<"it is not allowed try related course";
 }
 }
 else {
 cout << endl<<"Prerequests not satisfied ,try some other related course "<<endl;
 }
 break;
 
 case 10:
 cout << "Print Graph Operation -" << endl;
 g.printGraph();
 break;
 
 case 11:
 cout<<"COURSES WE OFFER !"<<endl;
 display();
 
 break;
case 12:
cout<<"Press '1 for student login' or 'press 0 for admin login' "<<endl;
cin>>login;
if (login==true){
do {
 cout << "What operation do you want to perform? " <<
 " Select Option number. Enter 0 to exit." << endl;
 cout << "1. Check if 2 courses are linked" << endl;
 cout << "2. Print All linked courses of a course" << endl;
 cout << "3. Next level"<<endl;
 cout << "4.display courses"<<endl;
 cout << "0. Exit Program" << endl;
 cin >> option;
 Vertex v1;
 switch (option) {
 case 0:
 break;
 
 case 1:
 cout << "Check if 2 courses are linked -" << endl;
 cout << "Enter ID of Source Course: ";
 cin >> id1;
 cout << "Enter ID of Destination Course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout << "courses are linked (Edge exist)";
 } else {
 cout << "courses are not linked (Edge does NOT exist)";
 }
 break;
 case 2:
 cout << "Print All linked course -" << endl;
 cout << "Enter ID of Course to fetch all linked courses : ";
 cin >> id1;
 g.getAllNeigborsByID(id1);
 break;
 
 case 3:
 cout << "Enter ID of your present course: ";
 cin >> id1;
 cout << "Enter ID of your next course: ";
 cin >> id2;
 check = g.checkIfEdgeExistByID(id1, id2);
 if (check == true) {
 cout<<"enter your mark"<<endl;
 cin>>mark;
 if(mark>=w){
 id1==id2;
 cout << "congratulations you are enrolled";
 }
 else if(mark<w){
 cout<<endl<<"your mark is low to do "<<cname<<endl;
 cout<<endl<<"you are not enrolled "<<endl;
 }
 else{
 cout<<"it is not allowed try related course";
 }
 }
 else {
 cout << endl<<"Prerequests not satisfied ,try some other related course "<<endl;
 }
 break;
 
case 4:
 cout<<"COURSES WE OFFER !"<<endl;
 display();
 break;
 
 default:
 cout << "Enter Proper Option number " << endl;
 }
 cout << endl;
 } while (option != 0);
 return 0;
}
 
default:
cout << "Enter Proper Option number " << endl;
 }
 // cout << endl;
 } while (option != 0);
}
else{
cout<<"Incorrect password"<<endl;
}
}
return 0;
}
