# MLS Dictionary

## C

<details>
  <summary>Confirmation Tag</summary>
  
  ...
</details>

<details>
  <summary>Confirmed Transcript Hash</summary>
  
  A running hash over the whole history of Commit messages, up to and including the signature of the most recent Commit.
  Commit messages are included directly. Proposal messages are indirectly included via the Commit that applied them.
  Both types of message are included by hashing the MLSAuthenticatedContent object in which they were sent.
</details>

## I

<details>
  <summary>Interim Transcript Hash</summary>
  
  A hash that covers the confirmed transcript hash plus the confirmation tag of the most recent Commit.
</details>

## U

<details>
  <summary>Unmerged Leaf</summary>
  
  ...
</details>
