## Git commit strategy

**1. Commit Frequency**
- Commit `often` and `early`. 
- Frequent commits help in keeping track of changes incrementally and make it easier to locate and understand changes, or revert them if necessary.

**2. Atomic Commits**
- Each commit **should represent <ins>a single logical change</ins>**. 
- This makes the commit history easier to understand and debug. 

**3. Commit Messages**
- Good commit messages are critical. 
- They <ins>**should clearly explain what the commit does and why the change is needed**</ins>, not just what was changed.

**4. Branching Strategy**
- **Ex1**: Feature Branch Workflow: Developers create branches for each new feature, keeping the main branch clean.
- **Ex2**: branching model designed around project releases, which distinguishes between different types of branches: feature, release, and hotfix.

**5. Commit Revisions**
- `Before` committing, it's good practice **to use git diff to review your changes** or git add -p to interactively choose chunks of code to commit. 
- This helps in <ins>**making sure only intended changes are committed**</ins>.

**6. Squashing and Rebase**
- `Squashing` turns <ins>**many commits into a single commit</ins>**, which can make the history cleaner and more understandable. 
- `Rebasing` is another technique used to **maintain a clean project history by moving or <ins>combining a sequence of commits to a new base commit</ins>**.

**7. Commit Tags**
- `Tags` are typically **used for marking releases** (v1.0, v2.0) and are immutable points that <ins>can help in rolling back to stable states in production</ins>.
