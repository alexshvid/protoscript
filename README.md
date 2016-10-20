# protoscript
protoscript

### Concept of the language 

##### Module operation

c = | a - b | 

### Example

```
package tutorial;

option java_package = "com.example.tutorial";
option java_outer_classname = "AddressBookProtos";

message Person {
  required string name = 1;
  required int32 id = 2;
  optional string email = 3;
  optional int32 visits = 4;

  enum PhoneType {
    MOBILE = 0;
    HOME = 1;
    WORK = 2;
  }

  message PhoneNumber {
    required string number = 1;
    optional PhoneType type = 2 [default = HOME];
  }

  repeated PhoneNumber phone = 4;
}

optional int32 increment(optional int32 id) = 101 {
  return id + 1; 
}

void Person:increment() = 1 {
  this.visits++;
}

required string Person:get_info() = 2 {
  return this.name + ", visits=" + this.visits;
}

void Person:set_name(required string name) = 3 {
  this.name = name;
}

void Person:set_email(optional string name) = 4 {
  this.email = email;
}

required int32 Person:get_id_plus_visits() = 5 {
  required int32 v = this.visits | 0;
  return this.id + this.visits;
}

optional int32 Person:mul() = 10 {
 optional int32 val = this.id * this.visits;
 return val;
}

required Person Person:new() = 6 {
  required Person p = {
     this.name = "";
     this.id = 0;
  }
  return p;
}

optional Person create_person(required string name, optional int32 id) = 77 {
  optional Person p = {
     this.name = name;
     this.id = id;
  }
  return p;
}


```

