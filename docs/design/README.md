# Проєктування бази даних

В рамках проекту розробляється: 
## модель бізнес-об'єктів 

@startuml

entity Query
entity Query.created #ffffff
entity Query.modified #ffffff
entity Query.id #ffffff
entity Query.title #ffffff
entity Query.description #ffffff

entity Source
entity Source.template #ffffff

entity Result
entity Result.id #ffffff
entity Result.name #ffffff
entity Result.description #ffffff

entity User
entity User.name #ffffff
entity User.email #ffffff
entity User.login #ffffff
entity User.password #ffffff

entity Access

entity Role
entity Role.name #ffffff
entity Role.description #ffffff

Query.created --* Query
Query.modified --* Query
Query.id --* Query
Query.title --* Query
Query.description --* Query

Result.id --* Result
Result.name --* Result
Result.description -l-* Result

Role.name -u-* Role
Role.description -u-* Role

Source.template -l-* Source

User.email -u-* User
User.name -u-* User
User.login -r-* User
User.password --* User


Query "0,*" -d- "0,*" Access

Query "0,*" -r- "1,1" Source

Query "0,*" -- "1,1" Result

User "1,1" -u- "0,*" Access
Role "1,1" -l- "0,*" Access

@enduml

## ER-модель

@startuml
  entity User <<ENTITY>> {
    name:VARCHAR
    email:VARCHAR
    login:VARCHAR
    password:VARCHAR
  }
  
  entity Role <<ENTITY>> {
    name:VARCHAR
    description:VARCHAR
  }
  
  entity Access <<ENTITY>> {
  
  }
  
  entity Query <<ENTITY>> {
    id:INT
    title:VARCHAR
    description:VARCHAR
    created:DATETIME
    modified:DATETIME
  }
  
  entity Source <<ENTITY>> {
    template:VARCHAR
  }
  
  entity Result <<ENTITY>> {
    id:INT
    name:VARCHAR
    description:VARCHAR
  }
  
Query "0," -d- "0," Access
Query "0,*" -r- "1,1" Source
Query "0,*" -- "1,1" Result
User "1,1" -u- "0," Access 
Role "1,1" -l- "0," Access
@enduml
  
## EER-модель
  
<blockquote class="imgur-embed-pub" lang="en" data-id="a/J07CI1J" data-context="false" ><a href="//imgur.com/a/J07CI1J"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>
