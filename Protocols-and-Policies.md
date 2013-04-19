## Reviewing
1. A developer MUST tag the reviewer that is expected to review.
1. A developer MUST, and only a developer CAN, change the issue labels to the appropriate `-pending` labels after new changes have been pushed.
1. A reviewer is expected to have finished review after a maximum of **12 hours** from being tagged.
1. A developer MAY tag the reviewer of the preceding component if the first reviewer fails to reply in the **12 hour** period.
1. A reviewer MAY or MAY NOT reply to a review request made **less than 6 hours** before a submission deadline.
1. A reviewer MUST, and only a reviewer CAN, change the issue labels to the appropriate `-reopen` or `-verified` labels after finishing reviewing.
1. All issue discussion SHOULD happen on the issue and not the pull request except for inline comments.
1. In case of the inline comments mentioned above the reviewer must inform the developer on the issue page of their existence.
1. All label changes MUST be announced in issue comments.
1. A reviewer MUST follow the appropriate [Reviewing Guidelines](https://github.com/DevYah/coolsoft-13/wiki/Conventions-and-Guidelines#reviewing)
    - A code reviewer MUST ensure that code is up to the [Code Standard](https://github.com/DevYah/coolsoft-13/wiki/Conventions-and-Guidelines#code-style-and-conventions) and does not contain any [Common Errors](https://github.com/DevYah/coolsoft-13/wiki/Common-Coding-Errors)
    - A documentation reviewer MUST ensure that documentation follows the [Standard](https://github.com/DevYah/coolsoft-13/wiki/Conventions-and-Guidelines#documentation) closely.

## Standup Meetings
1. All developers MUST push their branches before starting the standup meeting.
1. Necessary questions to be answered by each developer:   
    - What have you done up to this meeting?
    - What problems have you faced?
    - What will you do till the next meeting?
1. The rest of the meeting is left to the component's discretion but should not overshoot the 15-20 minute mark.

## Progress
1. A developer that has completed a task MUST award points to themselves in the Sprint Backlog entry for the next upcoming meeting. The points MUST be backed up by a commit that has happened before the meeting and was pushed.
1. A developer that has shown no progress for more than **2 consecutive** meetings stands the risk of reshuffling.

## Pull Requests
1. A pull request for a branch SHALL ONLY be made once the branch is ready to be at least scenario and code reviewed.
1. A pull request description MUST reference the issue(s) that it addresses and the reviewers that are expected to review.
1. A pull request MUST be mergeable to start with. The last commit in a pull request MUST be a merge master commit, unless master has not been updated since the last merge.
1. A pull request MUST be accepted/merged by the last reviewer to verify the pull request.

### Topic Branches 
1. There MAY be topic branches that compromise no more than 4 issues each which would conflict with each other otherwise.
1. **Only one** pull request for the entire topic branch is required.
1. A topic branch pull request description MUST reference the issues that are addressed and all reviewers that are expected to review.
1. A topic branch pull request MAY NOT be merged unless all constituent issues are verified by the respective reviewers.