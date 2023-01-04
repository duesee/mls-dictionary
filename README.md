# MLS Dictionary (draft-ietf-mls-protocol-16)

## C

<details>
  <summary><a name="concept_commit">Commit</a></summary>
  
...
</details>

<details>
  <summary><a name="concept_commit_secret">Commit secret</a></summary>
  
  `path_secret[n+1]`
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
  
  The copath of a node is the node's sibling concatenated with the list of siblings of all the nodes in its direct path, excluding the root.
  
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
  
  The direct path of a root is the empty list, and of any other node is the concatenation of that node's parent along with the parent's direct path.
  
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
  
  The filtered direct path of a leaf node L is the node's [direct path](#concept_direct_path), with any node removed whose child on the [copath](#concept_copath) of L has an empty [resolution](#concept_resolution) (keeping in mind that any [unmerged leaves](#concept_unmerged_leaf) of the copath child count toward its resolution). The removed nodes do not need their own key pairs because encrypting to the node's key pair would be equivalent to encrypting to its non-copath child.
  
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

## K

<details>
  <summary><a name="key_package">Key package</a></summary>
  
  A (signed) data structure containing (pre-published) public information about a user. Notably, it contains a public key ("init key") that others can use to encrypt a [Welcome message] to this user. It also contains the content of the [leaf node] that should be added to the tree representing the user.
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
  
  ```c
  struct {
      opaque kem_output<V>;
      opaque ciphertext<V>;
  } HPKECiphertext;

  struct {
      HPKEPublicKey encryption_key;
      HPKECiphertext encrypted_path_secret<V>;
  } UpdatePathNode;

  struct {
      LeafNode leaf_node;
      UpdatePathNode nodes<V>;
  } UpdatePath;

  struct {
      ProposalOrRef proposals<V>;
      optional<UpdatePath> path;
  } Commit;
  ```
  
  Only add, psk, reinit proposals do not require path.
  
</details>
