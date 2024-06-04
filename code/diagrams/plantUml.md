Tool to create diagrams from plain text descriptions such as UML diagrams, sequence diagrams, class diagrams etc. Full documentation can be found here - https://plantuml.com
# Examples
## Sequence Diagram
```plantuml
User -> FE: Request 
FE -> BE: Process Request 
BE -> DB: Query Data 
DB -> BE: Return Data 
BE -> FE: Send Response 
FE -> User: Display Data
```

## Activity Diagram
```plantuml
start 
:User logs in; 
:Display dashboard; 
if (User wants to add item?) then (yes) 
	:Add item to cart; 
else (no) 
	:Browse products; 
endif 
:User checks out; 
stop
```
## Class Diagram
```plantuml
class User { 
	+String name 
	+String email 
	+login() 
	+logout() 
} 

class Product { 
	+String name 
	+float price 
	+addToCart() 
}
```
