# MLS Dictionary (draft-ietf-mls-protocol-16)

## C

<details>
  <summary><a name="concept_commit">Commit</a></summary>
  
...
</details>

<details>
  <summary><a name="concept_confirmation_tag">Confirmation tag</a></summary>
  
  A MAC over the [confirmed transcript hash](#concept_confirmed_transcript_hash) (calculated by using the `confirmation_key`).
  It confirms that the members of the group have arrived at the same state of the group, because the confirmed transcript hash covers every commit and (although indirectly) every proposal.
</details>

<details>
  <summary><a name="concept_confirmed_transcript_hash">Confirmed transcript hash</a></summary>
  
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
  <summary><a name="concept_descendants">Descendants (of a node)</a></summary>
  
  ...
</details>


<details>
  <summary><a name="concept_direct_path">Direct path (of a node)</a></summary>
  
  ### Example:

  ![Direct path from node A (Diagram)](direct_path.mmd)
</details>

## E

<details>
  <summary><a name="concept_external_commit">External commit</a></summary>
  
  A mechanism for new members (external parties that want to become members of the group) to add themselves to a group, without requiring that an existing member has to come online to issue a Commit that references an Add Proposal. New members can create an External Commit if they have access to the current group info (that contains an ExternalPub extension). External Commits work like regular Commits, however, their content has to meet a specific set of requirements.
</details>

<details>
  <summary><a name="proposal_external_init">ExternalInit (Proposal)</a></summary>
  
  A proposal used by new members to join a group by using an [external commit](#concept_external_commit). This proposal can only be used in that context.
</details>

## F

<details>
  <summary><a name="concept_filtered_direct_path">Filtered direct path (of a node)</a></summary>
  
  TODO: Broken example.
  
  ### Example:

  ![Filtered direct path from node A (Diagram)](filtered_direct_path.mmd)
</details>

<details>
  <summary><a name="term_full_commit">"Full" commit</a></summary>
  
  A commit that contains a `path` field (see [Update path](#concept_update_path)).
</details>


## I

<details>
  <summary><a name="concept_interim_transcript_hash">Interim transcript hash</a></summary>
  
  A hash that covers the [confirmed transcript hash](#concept_confirmed_transcript_hash) plus the [confirmation tag](#concept_confirmation_tag) of the most recent Commit.
</details>

## P

<details>
  <summary><a name="concept_proposal">Proposal</a></summary>
  
...
</details>

## R

<details>
  <summary><a name="concept_resolution">Resolution (of a node)</a></summary>
  
  An ordered list of non-blank nodes that collectively cover all non-blank [descendants](#concept_descendants) of the node.
</details>

## U

<details>
  <summary><a name="concept_unmerged_leaf">Unmerged leaf</a></summary>
  
  The unmerged leaves array is a bookkeeping procedure to remember leaves that were added after a node was last updated.
  Used in resolution and parent-hash verification. (Description shamelessly copied from an email Théophile Wallez wrote to mls@ietf.org.)
</details>

<details>
  <summary><a name="concept_update_path">Update path</a></summary>
  
  ...
</details>
