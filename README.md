# MLS Dictionary (draft-ietf-mls-protocol-16)

## C

<details>
  <summary>Confirmation Tag</summary>
  
  ...
</details>

<details>
  <summary>Confirmed Transcript Hash</summary>
  
  A running (chained) hash over the whole history of `Commit` messages including the most recent `Commit`. 
  `Proposal`s are indirectly included through the `ProposalRef`s in the `Commit` that applied them.
  The hash of a `Commit` (and a `Proposal` to obtain a `ProposalRef`) is calculated over the `MLSAuthenticatedContent` in which it was sent.
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
