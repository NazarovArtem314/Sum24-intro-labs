# Lab 1: Introduction to DevOps with Git

## Task 1: SSH Commit Signature Verification

The signing of commits helps to increase safety and, as a result, the reliability of the code, ensuring the confidence that the changes were made by a specific user.

We use ssh:
* SSH is easy to generate.
* A GPG key can expire or be revoked when no longer used. GitHub shows commits that were signed with such a key as "Verified" unless the key was marked as compromised. SSH keys don't have this capability.
* GPG has features that SSH does not.

## Task 2: Merge Strategies in Git

1. Standard Merge: Combines two branches by creating a merge commit.
    - **Advantages**:
        * Save the full history and chronological order.
        * Supports the context of the branch.
    - **Disadvantages**:
        * The history of commits can be filled with many small commits.

2. Squash and Merge: Combines all commits from a feature branch into a single commit before merging.
    - **Advantages**:
        * The history of the changes is more pure and understandable, due to the unification of several small commits in one.
    - **Disadvantages**:
        *  Lose information about when specific changes were originally made and who authored the squashed commits.
        * Some Git commands that use the "SHA" or "hash" ID may be harder to use since the SHA ID for the original commits is lost. For example, using git rerere may not be as effective.

3. Rebase and Merge: Reapplies commits from a feature branch onto the base branch.
    - **Advantages**:
        * The history of commits looks more linear.
    - **Disadvantages**:
        * Rebase changes the history of commits.
        * Rebase can cause many conflicts.
        * Rebase can be risky.
        * When using the Rebase and Merge option on a pull request, it's important to note that the commits in the head branch are added to the base branch without commit signature verification. 


