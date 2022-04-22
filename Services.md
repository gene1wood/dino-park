# DinoPark * Services

These routes would be prefixed by a URL like https://people.mozilla.org/. For 
example the **/api/v4/orgchart** route for DinoPark Fence would be 
https://people.mozilla.org/api/v4/orgchart

## DinoPark Fence

Profile API and proxy to search and orgchart – https://github.com/mozilla-iam/dino-park-fence

### Routes
- _(public)_ **/api/v4/graphql**
- _(public)_ **/api/v4/search/simple/**
- **/api/v4/orgchart**
- **/api/v4/orgchart/trace/_{username}_**
- **/api/v4/orgchart/related/_{username}_**
- **/_/login**
- **/_/logout**

---

## DinoPark Fossil

Picture API – https://github.com/mozilla-iam/dino-park-fossil

### Routes
- _(public)_ **/avatar/get/id/_{filename}_**
- **/avatar/send/intermeditate**
- _(internal)_ **/internal/save/_{uuid}_**
- _(internal)_ **/internal/display/_{uuid}_**

---

## DinoPark Whoami

Verified Identities API – https://github.com/mozilla-iam/dino-park-whoami

### Routes
- _(public)_ **/whoami/github/username/_{id}_**
- **/whoami/github/add**
- **/whoami/github/auth**
- **/whoami/bugzilla/add**
- **/whoami/bugzilla/auth**

---

## DinoPark Lookout

Handles web hooks for profile updates – https://github.com/mozilla-iam/dino-park-lookout

### Routes
- **/events/update**
- _(internal)_ **/internal/update**
- _(internal)_ **/internal/bulk**

---

## DinoPark Packs

Access Groups Management API – https://github.com/mozilla-iam/dino-park-packs

### Routes

https://app.swaggerhub.com/apis/fiji/dinoparkgroups/1.0.0-oas3#/default

- **/info/groups** : GET : groups from token vs group service
- **/groups/api/v1/groups** : POST : create a group
- **/groups/api/v1/groups** : GET : paginated groups
- **/groups/api/v1/groups/{groupName}** : GET : group information
- **/groups/api/v1/groups/{groupName}** : PUT : updates a group
- **/groups/api/v1/groups/{groupName}** : DELETE : deletes a group
- **/groups/api/v1/groups/{groupName}/details** : GET : detailed group information
- **/groups/api/v1/terms/{groupName}** : GET : group terms
- **/groups/api/v1/terms/{groupName}** : DELETE : delete group terms
- **/groups/api/v1/terms/{groupName}** : POST : create group terms
- **/groups/api/v1/terms/{groupName}** : PUT : update group terms
- **/groups/api/v1/requests/{groupName}** : GET : group invitation requests
- **/groups/api/v1/requests/{groupName}/{userUuid}** : reject an invitation request
- **/groups/api/v1/invitations/{groupName}** : GET : group invitations
- **/groups/api/v1/invitations/{groupName}** : POST : invite a member
- **/groups/api/v1/invitations/{groupName}/email** : GET : group invitation email copy
- **/groups/api/v1/invitations/{groupName}/email** : POST : set group invitation email copy
- **/groups/api/v1/invitations/{groupName}/{userUuid}** : PUT : update an invitation
- **/groups/api/v1/invitations/{groupName}/{userUuid}** : DELETE : delete an invitation
- **/groups/api/v1/members/{groupName}** : GET : paginated members
- **/groups/api/v1/members/{groupName}/{memberUuid}** : DELETE : delete a member
- **/groups/api/v1/members/{groupName}/{memberUuid}/renew** : POST : renew a member
- **/groups/api/v1/curators/{groupName}** : POST : add a curator
- **/groups/api/v1/curators/{groupName}/{memberUuid}/downgrade** : POST : downgrade a curator to a normal member
- **/groups/api/v1/users** : GET : search for users
- **/groups/api/v1/users/any** : GET : search for any users
- **/groups/api/v1/self/{groupName}** : DELETE : leave a group
- **/groups/api/v1/self/requests** : GET : invitation requests from the logged in user
- **/groups/api/v1/self/requests/{groupName}** : POST : request to be invited
- **/groups/api/v1/self/requests/{groupName}** : DELETE : cancel a request to be invited
- **/groups/api/v1/self/invitations** : GET : invitations for the logged in user
- **/groups/api/v1/self/invitations/{groupName}** : POST : join a group
- **/groups/api/v1/self/invitations/{groupName}** : DELETE : reject an invitation to a group
- **/groups/api/v1/sudo/member/{groupName}** : POST : add a member
- **/groups/api/v1/sudo/logs/all/raw** : GET : returns an audit log containing records of all actions taken on groups over time
- **/groups/api/v1/sudo/mail/nda/{userUuid}** : POST : subscribe user to nda mailing list
- **/groups/api/v1/sudo/mail/nda/{userUuid}** : DELETE : unsubscribe user to nda mailing list
- **/groups/api/v1/sudo/curators/{groupName}** : GET : curators for a given group
- **/groups/api/v1/sudo/curators/{groupName}** : POST : add a curator to a given group
- **/groups/api/v1/sudo/user/{userUuid}** : DELETE : delete a user
- **/groups/api/v1/sudo/user/inactive** : DELETE : delete inactive users
- **/groups/api/v1/sudo/user/consolidate** : DELETE : send all group members to CIS to consolidate (note: this treats DinoPark as source of truth).
- **/groups/api/v1/sudo/user/uuids/members** : GET : all member's UUIDs
- **/groups/api/v1/sudo/user/uuids/staff** : GET : all staff's UUIDs
- **/groups/api/v1/sudo/user/data/{userUuid}** : GET : all profile and group data for a given UUID
- **/groups/api/v1/sudo/user/cis/{userUuid}** : POST : update CIS with a user's current groups
- **/groups/api/v1/sudo/member/{groupName}** : POST : add member to group
- **/groups/api/v1/sudo/member/{groupName}/{userUuid}** : DELETE : remove member from group
- **/groups/api/v1/sudo/trust/groups/{groupName}** : PUT : change the trust level of a group (e.g. from staff to nda) note that increasing the trust level will kick out members that don't have this trust level.
- **/groups/api/v1/sudo/groups/inactive** : GET : list inactive groups
- **/groups/api/v1/sudo/groups/inactive/{groupName}** : DELETE : delete inactive or reserved group
- **/groups/api/v1/sudo/groups/reserve/{groupName}** : POST : reserves a group name for future use so it cannot be created
- **/groups/api/v1/sudo/transfer** : POST : transfer access groups from user a to user b. This is used for offboarding staff or people that lost their account.
- **/groups/api/v1/forms/email/** : GET : simple html form to send emails
- **/groups/api/v1/forms/email/bcc** : POST : send email on behalf of DinoPark
- **/groups/api/v1/forms/email/group** : POST : send email to a group

---

## DinoPark Search

Search API – https://github.com/mozilla-iam/dino-park-search

### Routes
- (internal) **/search/simple/_{scope}_/**
- (internal) **/search/update**
- (internal) **/search/delete/_{uuid}_/**
- (internal) **/search/uuid/_{user_id}_/**
- (internal) **/search/bulk**
- (internal) **/search/recreate**

---

## DinoPark Tree

Orgchart API – https://github.com/mozilla-iam/dino-park-tree

### Routes
- (internal) **/orgchart**
- (internal) **/orgchart/related/_{username}_**
- (internal) **/orgchart/directs/_{username}_**
- (internal) **/orgchart/trace/_{username}_**
- (internal) **/orgchart/expanded/_{username}_**
- (internal) **/orgchart/update**
- (internal) **/orgchart/delete/_{uuid}_/**
- (internal) **/orgchart/bulk**
- (internal) **/orgchart/recreate**

---

## DinoPark World

Location (suggestion) API – https://github.com/mozilla-iam/dino-park-world

### Routes
- **/world/suggest*
- (internal) **/world/populate**
- (internal) **/world/recreate**

---