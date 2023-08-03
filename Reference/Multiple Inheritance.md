# Multiple Inheritance
Multiple Inheritance - that's a feauture of our C++ , where we can inherit characteristics (data members and functions) from parents classes. There's a syntax :
```c++

class NameOfClass: [access-specifier] ParentsClass{  //, [access-specifier] ParentsClass2 , you can add more than one parents class
        //code
}
```
Here's we got functions and data members depending of access specifier we wrote, it can be : ```public```, ```private``` or ```protected```. Here's an example of this:
```c++
class Jupiter{ // created a class
public:    //access-specifier is public
    void NoSurface(){
      std::cout << "I have no Surface\n"; //indeed, that's a gas planet
   }
};
class Neptune{
public:
      void Rings(){
        std::cout << "I have rings!"; //not to marry 
    }
};

class Saturn: public Jupiter, public Neptune { // class Satun took things(functions in our example) from public Jupiter and Nepture
      void Name(){
        std::cout << "*loud planet sounds*\n"; //added something own 
    }
};
//Now let's print them out

int main(){
      Saturn PlanetSaturn; //creating our planet with name 'PlanetSaturn'
      //now what we have? if we write 'PlanetSaturn.' (with dot), we will see that we can use functions Rings() and NoSurface(), from our parents
      PlanetSaturn.Name(); //Output: *loud planet sounds*
      PlanetSaturn.NoSurface(); //Output: I have no Surface (from the class Jupiter)
      PlanetSaturn.Rings(); //Output: I have rings! (from the class Nepture) 
}
```
### Problem with Multi Inheritance
Let's imagine this situation:
```c++
class VideoGame{
public:
      void open(){
        std::cout << "You've launched a video game!\n";
      }
};

class Project{
public:
      void open(){
         std::cout << "You've opened a project, ready to work!\n";
      }
};

class Person: public VideoGame, public Project{}; //this class has nothing own



int main(){
      //Let's create a Person class to launch a project
      Person person;
      person.open(); //ERROR: what open() function do you use? from 'VideoGame' class or 'Project'?
}
```
As you see, there's a misunderstanding with compiler about what class do you choose to launch 'open'. Do you want to play Video Game or work on a Project? 😏
<br>To fix that problem you can move a function to ```private```, and create a new function in ```public```, which launches a function from ```private``` </br>
```c++
class VideoGame{
private:
      void open(){
        std::cout << "You've launched a video game!\n";    //we moved this function to private
      }
public:
      void launchTheGame(){
        open();                                           // launching open() function from private
      }
};

class Project{
public:
      void open(){
         std::cout << "You've opened a project, ready to work!\n";
      }
};

class Person: public VideoGame, public Project {}; //this class has nothing own



int main(){
      //Let's create a Person class to launch a project
      Person person;
      person.open(); //Output: You've opened a project, ready to work!
      person.launchTheGame(); //Output: You've launched a video game!

}
```
