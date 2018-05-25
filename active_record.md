Classes corresponding to => Table
Intances corresponding to => row/record


* Define a model Class
     * Singular version of the pluralized table names
     * Capitalized/ Camel Cases
     * Inherite from ActiveRecord::Base

/***************** we will recieve a single record *******************/
     * Student.Create()  Saves to database automically
     * s- Student.new() creates a new instance but don't save until
                         you call the .save method
     * s.save
     * Student.find(some_id)
     * Student.find_by(search_by_attribute/colomn_names)

  /***************** we will return multiple record/instances *******************/  

     * Student.where(attribute/column_names.to_search_by)


     * my_student= Student.find(1)

     * my_student.update(.........) update it in the database

       /*********will update the instace but won't update the database until you call save ********/

     my_student.first_name = ............    
     my_student.save

     my_student.destroy
     Student.destroy(id)
     Student.destroy_all


/*****************Relationship 1 to 1 ****************************/
/***************Student**********************Laptop****************/            

      ClassA - id
      ClassB id, class_a_id

      ClassB

          belongs_to :class_a

      end
      ClassA

        has_one :class_b

      end

/*****************Relationship 1 to m ****************************/
/***************Student**********************Records****************/  

      Relationship 1 to m            

            ClassA - id
            ClassB id, class_a_id

            ClassA

                has_many :class_bs   (plural)

            end

            a=ClassA.find(...)
            a.class_bs

            ClassB

                belongs_to :class_a

            end
            b= ClassB.find()
            b.class_a




/***********************   Releationship many to many relationship ***********************/

-----------Person-----------Personcar-------------------Cars---------


           class Person

              has_many :person_cars
              has_many :cars, through: : person_cars

           end

           class PersonCar

               belongs_to :person
               belongs_to : car

           end

           class Car

              has_many :person_cars
              has_many :persons, through: :person_cars

           end


has_many :cars, through: : person_cars


       my_person = Person.find(7)
       my_person.cars << car.find(10)
       my_person.cars
