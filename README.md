# Hotel_Pr
This program collects hotel data (location, number of floors, number of rooms per floor, occupancy info), calculates: total income,total rooms,total occupied / unoccupied rooms,occupancy rate,the floor with the fewest rooms, and whether occupancy needs improvement. Finally, it prints a formatted summary report.

#include<iostream>
#include<string>
#include<iomanip>
#include<cstdlib>
#include<math.h>
using namespace std;
int main() {
    int highestfloor=1;
    int highestnumofrooms=0;
    const int singleroom=60;
    const int doubleroom=75;
    const int kingroom=100;
    const int suiteroom=150;
    string location;
    const int min_floor=1;
    const int max_floor=5;
    int rooms;
    const int min_rooms=1;
    const int max_rooms=30;
    int floors;
    int single_room;
    int double_room;
    int king_room;
    int suite_room;
    double total_amount=0;
    double total_number_of_rooms=0;
    int total_of_unoccupied_rooms=0;
    double total_of_occupied_rooms=0;
    double occupancy_rate;
    const int OCCUPANCY_IMRPOVE=60;
    cout<<"===============================================\n";
    cout<<"              BlueMont Hotel                \n";
    cout<<"===============================================\n";
    
    cout<<"Enter the location of this hotel chain:";
    getline(cin, location);//get line  will display the whole line/
    
    cout<<"Enter total number of floors of the hotel:";//this code will display the message//
    cin>>floors;//inputs user//
    
    cout<<endl;//this code is used for a line of sapce//
   
    while(floors<min_floor || floors>max_floor)//while loop is used to make sure that the user input has a range, if the user does not input around the range it will keep looping until the user enter the correct amount of floors//
    {
        cout<<"Number of floors should be between "<< min_floor<<" and "<< max_floor<<"!! "<<"Please try again."<<endl;
        cout<<endl;
        
        cout<<"Enter total number of floors of the hotel:";
        cin>>floors;
        
    }
    for(int i=0;i<floors;i++)//this code will increase the floor by one when the user inputs floor//
    {
      cout<<"Enter total number of rooms in the "<< i+1<<"th floor:";
        cin>>rooms;
    
        while(rooms<min_rooms || rooms>max_rooms)//while loop is used to make sure that the user input has a range, if the user does not input around the range it will keep looping until the user enter the correct amount of rooms//
        {
            cout<<endl;
            cout<<"Number of rooms should be between "<<min_rooms<<" out "<<max_rooms<<"!! "<<" Please try again.\n";
            cout<<endl;
            cout<<"Enter total number of rooms on floor "<< i+1<<":";
            cin>>rooms;
        }
        
        if (i==0)
        {
            
            highestfloor=1;
            highestnumofrooms=rooms;
        
        }
        
        cout<<"How many SINGLE rooms occupied in the " << i+1 << "th floor:";
            cin>>single_room;//user input //
            
        cout<<"How man DOUBLE rooms occuppied in the " << i+1  << "th floor:";
            cin>>double_room;//user input //
            
        cout<<"How many King rooms occuppied in the " << i+1 << "th floor:";
            cin>>king_room;//user input //
            
        cout<<"How many SUITE rooms occuppied in the " << i+1 << "th floor:";
            cin>>suite_room;//user input //
        cout<<endl;
       while(single_room+double_room+king_room+suite_room>=rooms){//while loop is used to make sure that the user input has a range, if the user does not input around the range it will keep looping until the user enter the correct amount of rooms for king,suite,single,and double//
          
           cout<<"Total number of occupied rooms exceeds the total number of rooms on this floor. Please try again";
           cout<<endl;
           cout<<"Enter total number of rooms on floor:";
           cin>>rooms;
           cout<<"How many SINGLE rooms occupied in the " << i+1 << "th floor:";
           cin>>single_room;
           cout<<"How many DOUBLE rooms occupied in the " << i+1 << "th floor:";
           cin>>double_room;
           cout<<"How man King rooms occuppied in the " << i+1 << "th floor:";
           cin>>king_room;
           cout<<"How man SUITE rooms occuppied in the " << i+1  << "th floor:";
          cin>>suite_room;
       }
            total_amount+=(singleroom*single_room)+(doubleroom*double_room)+(kingroom*king_room)+(suiteroom*suite_room);//this code here and below it is all the caculations//
        total_number_of_rooms+=rooms;//caculations to find total amount of rooms//
        total_of_occupied_rooms+=single_room+double_room+king_room+suite_room;//caculations to find total amount of occupied rooms//
        if(highestnumofrooms>rooms){
            highestnumofrooms=rooms;
            highestfloor=i+1;
        
        }//if statement used to test if the statement is true//
    }
    
    cout<<endl;
    
    cout<<"====================================================================================================\n";
    cout<<"BlueMont Hotel Located in "<< location <<endl;
    cout<<"====================================================================================================\n";
    cout<<"TODAY'S ROOM RATES<US$/night>"<<endl;
    cout<<"Single Room"<< setw(25) << "Double Room"<< setw(25) <<"King Room"<< setw(25) <<"Suite Room"<<endl;
    cout<<endl;
    cout<<setw(10)<<"60"<<setw(25)<<"75"<<setw(25)<<"100"<<setw(25)<<"150"<<endl;
    cout<<"====================================================================================================\n";
    total_of_unoccupied_rooms=total_number_of_rooms-total_of_occupied_rooms;
cout<<"Hotel Income:"<<setw(20)<<setprecision(2)<<fixed<<"$"<<total_amount<<endl;//setprecion is used to display the number of place holders after the decimal point. setw is used to display the amount of spaces you want it to display//
cout<<"Total number of rooms:"<<setprecision(0)<<fixed<<setw(16)<<total_number_of_rooms<<endl;
    
cout<<"Total number occupied rooms:"<<setw(10)<<setprecision(0)<<fixed<<total_of_occupied_rooms<<endl;
cout<<"Total number unoccupied:"<<setw(14)<<total_of_unoccupied_rooms<<endl;
occupancy_rate=(total_of_occupied_rooms*100/total_number_of_rooms);
cout<<"Occupancy rate"<<setw(25)<<setprecision(2)<<fixed<<occupancy_rate<<"%"<<endl;
cout<<endl;
cout<<highestfloor<<"th floor with "<<highestnumofrooms<<" rooms, has the least number of rooms."<<endl;
    if(occupancy_rate<OCCUPANCY_IMRPOVE){
        cout<<"Needs to improve Hotel occupancy rate!!";
        cout<<endl;
    }
cout<<endl;
    

    
    
    
    
    
    
return 0;
}





    
