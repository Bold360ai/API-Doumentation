@startuml

actor User
participant App
participant Nanorep

group Session Less
User -> App: First launch and select a topic (Label)
App -> Nanorep: Fetch configuration
note right
[[https://github.com/nanorepsdk/API-Doumentation/wiki/Configuration Configuration API]]
end note
Nanorep --> App: Set the UI according to the configuration
App -> Nanorep: Fetch FAQs according to the label selected
note right
[[https://github.com/nanorepsdk/API-Doumentation/wiki/FAQ-For-Label FAQ For Label API]]
end note
Nanorep --> App: Presnt FAQs

User -> App: Select FAQ
App -> Nanorep: Fetch FAQ article
note right
[[https://github.com/nanorepsdk/API-Doumentation/wiki/Article Article API]]
end note
Nanorep --> App: Present the article
end

User -> App: Type new query
alt No Session Id
App -> Nanorep: Create session
note right
[[https://github.com/nanorepsdk/API-Doumentation/wiki/Create-Session Create Session API]]
end note
App -> App: Keep Alive
note right
[[https://github.com/nanorepsdk/API-Doumentation/wiki/Keep-Alive Keep Alive API]]
end note
end
Nanorep --> App: Session has created and got a session id
App -> Nanorep: Fecth auto complete 
note right
[[https://github.com/nanorepsdk/API-Doumentation/wiki/Auto-Complete Auto Complete API]]
end note
Nanorep --> App: Present auto complete

User -> App: Selecte a query from the auto complete list
App -> Nanorep: Search the selected query
note right
[[https://github.com/nanorepsdk/API-Doumentation/wiki/Search Search API]]
end note
Nanorep --> App: Present the article 
note right
[[https://github.com/nanorepsdk/API-Doumentation/wiki/Article Article API]]
end note
@enduml
