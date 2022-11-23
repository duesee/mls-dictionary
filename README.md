# MLS Dictionary (draft-ietf-mls-protocol-16)

## C

<details>
  <summary><a name="concept_confirmation_tag">Confirmation Tag</a></summary>
  
  A MAC over the [confirmed transcript hash](#concept_confirmed_transcript_hash) (calculated by using the `confirmation_key`).
  It confirms that the members of the group have arrived at the same state of the group, because the confirmed transcript hash covers every commit and (although indirectly) every proposal.
</details>

<details>
  <summary><a name="concept_confirmed_transcript_hash">Confirmed Transcript Hash</a></summary>
  
  A running (chained) hash over the whole history of `Commit` messages including the most recent `Commit`. 
  `Proposal`s are indirectly included through the `ProposalRef`s in the `Commit` that applied them.
  The hash of a `Commit` (and a `Proposal` to obtain a `ProposalRef`) is calculated over the `MLSAuthenticatedContent` in which it was sent.
</details>

<details>
  <summary><a name="concept_copath">Copath (of a node)</a></summary>
  
  ### Example:

  ![Copath from node A (Diagram)](copath.mmd)
</details>

## D

<details>
  <summary><a name="concept_direct_path">Direct path (of a node)</a></summary>
  
  ### Example:

  ![Direct path from node A (Diagram)](direct_path.mmd)
</details>

## F

<details>
  <summary><a name="concept_filtered_direct_path">Filtered direct path (of a node)</a></summary>
  
  TODO: Broken example.
  
  ### Example:

  ![Filtered direct path from node A (Diagram)](filtered_direct_path.mmd)
</details>

## I

<details>
  <summary><a name="concept_interim_transcript_hash">Interim Transcript Hash</a></summary>
  
  A hash that covers the [confirmed transcript hash](#concept_confirmed_transcript_hash) plus the [confirmation tag](#concept_confirmation_tag) of the most recent Commit.
</details>

## R

<details>
  <summary><a name="concept_resolution">Resolution (of a node)</a></summary>
  
  An ordered list of non-blank nodes that collectively cover all non-blank descendants of the node.
</details>

## U

<details>
  <summary><a name="concept_unmerged_leaf">Unmerged Leaf</a></summary>
  
  ...
</details>
