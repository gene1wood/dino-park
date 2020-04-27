# DinoPark * Services

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