# MLS Dictionary (draft-ietf-mls-protocol-16)

## C

<details>
  <summary>Confirmation Tag</summary>
  
  A MAC (calculated by using the `confirmation_key`) over the confirmed transcript hash.
  It confirms that the members of the group have arrived at the same state of the group, because the confirmed transcript hash covers every commit (and indirectly also all proposal).
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
