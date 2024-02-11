#|-------------------------------------------------|
|                  User Table                     |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| _id              | ObjectId    | Primary Key| Yes  | Unique identifier               |
| Username         | String      |        | Yes      | User's username                 |
| email            | String      |        | Yes      | User's email                    |
| password         | String      |        | Yes      | Hashed password                 |
| gameConsole      | String      |        |          | User's preferred gaming console|
| IsActive         | Boolean     |        |          | User's active status            |
|-------------------------------------------------|

|-------------------------------------------------|
|                  Game Table                     |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| GameID           | ObjectId    | Primary Key| Yes  | Unique identifier               |
| Title            | String      |        | Yes      | Title of the game               |
| Genre            | String      |        |          | Genre of the game               |
| ReleaseDate      | Date        |        |          | Release date of the game        |
| Description      | String      |        |          | Description of the game         |
|-------------------------------------------------|

|-------------------------------------------------|
|               UserHistory Table                  |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| _id              | ObjectId    | Primary Key| Yes  | Unique identifier               |
| userID           | ObjectId    | Foreign Key (User)| Yes| References User              |
| interactions     | Array of Documents |      |          | Array storing user interactions|
|-------------------------------------------------|

|-------------------------------------------------|
|            DirectMessage Table                  |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| MessageID        | ObjectId    | Primary Key| Yes  | Unique identifier               |
| SenderID         | ObjectId    | Foreign Key (User)| Yes| References User (Sender)       |
| ReceiverID       | ObjectId    | Foreign Key (User)| Yes| References User (Receiver)     |
| Content          | String      |        | Yes      | Content of the message          |
| Timestamp        | Date        |        | Yes      | Timestamp of the message        |
|-------------------------------------------------|

|-------------------------------------------------|
|               Interaction Table                 |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| _id              | ObjectId    | Primary Key| Yes  | Unique identifier               |
| userID           | ObjectId    | Foreign Key (User)| Yes| References User              |
| igdbGameID       | ObjectId    | Foreign Key (Game)| Yes| References Game              |
| contentType      | String      |        | Yes      | Type of interaction             |
| content          | String      |        | Yes      | Content of the post or comment |
| datePosted       | Date        |        | Yes      | Date when the interaction was posted |
| dateDeleted      | Date        |        |          | Date when the interaction was deleted|
| dateUpdated      | Date        |        |          | Date when the interaction was updated|
| dateViewed       | Date        |        |          | Date when the interaction was viewed |
|-------------------------------------------------|

|-------------------------------------------------|
|               UserSearch Table                  |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| Searchid         | ObjectId    | Primary Key| Yes  | Unique identifier               |
| UserId           | ObjectId    | Foreign Key (User)| Yes| References User              |
| ResultUserId     | Array of Objects |          |          | Ids of Users                   |
|-------------------------------------------------|

|-------------------------------------------------|
|                Friendship Table                 |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| FriendshipID     | ObjectId    | Primary Key| Yes  | Unique identifier               |
| UserID1          | ObjectId    | Foreign Key (User)| Yes| References User (1st User)     |
| UserID2          | ObjectId    | Foreign Key (User)| Yes| References User (2nd User)     |
| Status           | String      |        | Yes      | Friendship status               |
|-------------------------------------------------|

|-------------------------------------------------|
|               Feedback Table                    |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| FeedbackID       | ObjectId    | Primary Key| Yes  | Unique identifier               |
| UserID           | ObjectId    | Foreign Key (User)| Yes| References User              |
| FeedbackContent  | String      |        |          | Feedback content                |
| DateSubmitted    | Date        |        |          | Date when the feedback was submitted |
|-------------------------------------------------|

|-------------------------------------------------|
|               GamePlay Table                    |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| PlayID           | ObjectId    | Primary Key| Yes  | Unique identifier               |
| UserID           | ObjectId    | Foreign Key (User)| Yes| References User              |
| GameID           | ObjectId    | Foreign Key (Game)| Yes| References Game              |
| DateTimeOfPlay   | Date        |        | Yes      | Date and time of the gameplay   |
|-------------------------------------------------|

|-------------------------------------------------|
|               Flag Table                        |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| FlagID           | ObjectId    | Primary Key| Yes  | Unique identifier               |
| UserID           | ObjectId    | Foreign Key (User)| Yes| References User              |
| PostID           | ObjectId    | Foreign Key (Interaction)|   | References Interaction (Post)|
| CommentID        | ObjectId    | Foreign Key (Interaction)|   | References Interaction (Comment)|
| Reason           | String      |        |          | Reason for flagging             |
| DateFlagged      | Date        |        |          | Date when the post/comment was flagged |
|-------------------------------------------------|

|-------------------------------------------------|
|               Announcement Table                |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| AnnouncementID   | ObjectId    | Primary Key| Yes  | Unique identifier               |
| AnnouncementContent| String    |        | Yes      | Content of the announcement     |
| DateCreated      | Date        |        | Yes      | Date when the announcement was created |
|-------------------------------------------------|

|-------------------------------------------------|
|               SystemActivityLog Table           |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| LogID            | ObjectId    | Primary Key| Yes  | Unique identifier               |
| ActivityDescription| String    |        | Yes      | Description of the activity     |
| UserID           | ObjectId    | Foreign Key (User)|   | References User (if applicable)|
| Timestamp        | Date        |        | Yes      | Timestamp of the activity       |
|-------------------------------------------------|

|-------------------------------------------------|
|               Report Table                      |
|-------------------------------------------------|
| Field            | Field Type  | Type   | Required | Description                      |
|------------------|-------------|--------|----------|----------------------------------|
| ReportID         | ObjectId    | Primary Key| Yes  | Unique identifier               |
| Type             | String      |        |          | Type of report                  |
| Description      | String      |        |          | Description of the report       |
|-------------------------------------------------|
