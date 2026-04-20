# PES-VCS Lab Report  
**Name:** Diya J Marar  
**SRN:** PES2UG24CS162 

---

# Overview
This project implements a simplified version control system (PES-VCS) inspired by Git. It demonstrates core concepts such as object storage, tree structures, staging area, and commit history.

---

# Phase 1: Object Storage

## Objective
Implement content-addressable storage using SHA-256 hashing.

## Implementation
- Implemented `object_write` and `object_read`
- Stored objects using SHA-256 hashing
- Used atomic file writing

## Output
![Screenshot 1A](images/phase1a.png)  
![Screenshot 1B](images/phase1b.png)

---

# Phase 2: Tree Objects

## Objective
Represent directory structure using tree objects.

## Implementation
- Built tree from index
- Stored hierarchical structure
- Ensured deterministic serialization

## Output
![Screenshot 2A](images/phase2a.png)  
![Screenshot 2B](images/phase2b.png)

---

# Phase 3: Index (Staging Area)

## Objective
Implement staging area for tracking file changes.

## Implementation
- Implemented `index_load`, `index_save`, `index_add`
- Stored file metadata and hashes

## Output
![Screenshot 3A](images/phase3a.png)  
![Screenshot 3B](images/phase3b.png)

---

# Phase 4: Commits

## Objective
Implement commit creation and history tracking.

## Implementation
- Implemented `commit_create`
- Linked commits using parent references
- Updated HEAD pointer

## Output
![Screenshot 4A](images/phase4a.png)  
![Screenshot 4B](images/phase4b.png)  
![Screenshot 4C](images/phase4c.png)

---

# Integration Test

![Integration](images/integration.png)

---

# Analysis Questions

## Q5.1
To implement checkout, update HEAD to the target branch, read its commit, extract the tree, and update the working directory. This is complex because it involves safely replacing files and handling uncommitted changes.

## Q5.2
Compare working directory files with index metadata. If a file is modified locally and differs in the target branch, block checkout to avoid conflicts.

## Q5.3
In detached HEAD, commits are not linked to a branch and may be lost. They can be recovered by creating a new branch pointing to the commit.

## Q6.1
Traverse from branch heads, mark reachable objects, and delete unmarked ones. A hash set is used for efficient tracking.

## Q6.2
GC during commit can delete newly created objects before they are referenced. Git prevents this using locking and safe reference updates.

---

# Conclusion
This project helped in understanding Git internals, including hashing, tree structures, staging, and commit management.
