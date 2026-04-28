[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/tfm_-hwX)

# Project 2: Moonlight Museum After Dark

## Team information
- Team name: Moonlight Coders  
- Members: Your Name  
- Repository name: ds26-p2-moonlight-museum  

---

## Project summary
Our project builds a system for organizing museum artifacts after dark. It uses multiple data structures to manage artifact storage, restoration requests, undo actions, exhibit routes, and reports. The system demonstrates how different data structures solve different real-world problems efficiently.

---

## Feature checklist

### Core structures
- [x] `Artifact` class/record
- [x] `ArtifactBST`
- [x] `RestorationQueue`
- [x] `ArchiveUndoStack`
- [x] `ExhibitRoute` singly linked list

### BST features
- [x] insert artifact
- [x] search by ID
- [x] preorder traversal
- [x] inorder traversal
- [x] postorder traversal
- [x] duplicate IDs ignored

### Queue features
- [x] add request
- [x] process next request
- [x] peek next request
- [x] empty check
- [x] size

### Stack features
- [x] push action
- [x] undo last action
- [x] peek last action
- [x] empty check
- [x] size

### Linked list features
- [x] add stop to end
- [x] remove first matching stop
- [x] list stops in order
- [x] count stops

### Utility/report features
- [x] category counts
- [x] unique rooms
- [x] sort by age
- [x] linear search by name

### Integration
- [x] `demo_museum_night()`
- [x] at least 8 artifacts in demo
- [x] demo shows system parts working together

---

## Design note (150-250 words)

This project uses multiple data structures to solve different parts of the museum system. A Binary Search Tree (BST) is used for storing artifacts because it allows efficient searching by artifact ID. Since IDs are unique and ordered, a BST makes it easy to insert and retrieve artifacts quickly.

A queue is used for restoration requests because requests must be handled in the order they arrive (FIFO). This ensures fairness and proper scheduling of work. A stack is used for undo actions because it follows a last-in, first-out (LIFO) pattern, which is ideal for reversing recent actions.

A singly linked list is used for the exhibit route because it represents a sequence of stops where each node points to the next location. This makes adding and removing stops efficient without needing to shift elements like in a list.

The system is organized into classes for each structure, keeping responsibilities separate and making the code easier to maintain. Helper functions handle reporting tasks such as counting categories and sorting artifacts.

---

## Complexity reasoning

- `ArtifactBST.insert`: O(h) where h is tree height, because insertion follows one path.
- `ArtifactBST.search_by_id`: O(h) because it searches down one branch.
- `ArtifactBST.inorder_ids`: O(n) because it visits every node once.
- `RestorationQueue.process_next_request`: O(1) using deque.
- `ArchiveUndoStack.undo_last_action`: O(1) using list pop.
- `ExhibitRoute.remove_stop`: O(n) because it may traverse the whole list.
- `sort_artifacts_by_age`: O(n log n) due to sorting.
- `linear_search_by_name`: O(n) because it checks each item.

---

## Edge-case checklist

### BST
- [x] insert into empty tree → creates root
- [x] search for missing ID → returns None
- [x] empty traversals → returns empty list
- [x] duplicate ID → ignored

### Queue
- [x] process empty queue → returns None
- [x] peek empty queue → returns None

### Stack
- [x] undo empty stack → returns None
- [x] peek empty stack → returns None

### Exhibit route linked list
- [x] empty route → handled safely
- [x] remove missing stop → returns False
- [x] remove first stop → updates head
- [x] remove middle stop → links adjusted
- [x] remove last stop → handled correctly
- [x] one-stop route → handled properly

### Reports
- [x] empty artifact list → returns empty structures
- [x] repeated categories → counted correctly
- [x] repeated rooms → handled using set
- [x] missing artifact name → returns None
- [x] same-age artifacts → sorted correctly

---

## Demo plan / how to run

Run tests:
```bash
pytest -q