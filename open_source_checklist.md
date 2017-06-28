# Open source checklist
Before going live with a public repository, the following considerations should be taken. 

## Required
- [ ] **Has PII been removed?**
  - Use [Clouseau](https://github.com/virtix/clouseau) for scanning source code.
  - If there are images, visually inspect each image to ensure there is no GSA-specific information.
    - Probably need to point people to PII list/definition
      - Look in [18F Before Your Ship](https://before-you-ship.18f.gov/)
      - Look at 18F seeker
- [ ] **Have security vulnerabilities been remediated?**
    - What are security vulnerabilities?
      - Passwords
    - What is sensitive?
    - What can be discussed in a public issue
      - Look in [18F Before Your Ship](https://before-you-ship.18f.gov/)
    - What about security management features such as security keys, encryption and decryption business logic?
- [ ] **Are we including any other open source products? If so, is there any conflict with our public domain release?**
    - Needs clarification in GSA
    - Are you using GPL code?
- [ ] **Is our `README.md` template with project information included?**   
    - Standard README needs to be created for all GSA   
    - Are installation instructions clearly written in the `README` _and_ tested on a clean machine?   
    - Are all dependencies described in the `README`, `requirements.txt`, and/or `buildout.cfg`?   
    - Is there a screenshot in the `README`, if applicable?
- [ ] **Is our `CONTRIBUTING.md` included?**
    - Standard CONTRIBUTING needs to be created for all GSA
- [ ] **Is our `LICENSE.md` included?**
    - Standard License needs to be created for all GSA
- [ ] **Is our `codeinventory.yml` included?**
    - This will help GSA take stock of the projects
- [ ] **Does the app source code contain 3rd party libraries or frameworks that are not open source (or have a different license?**
- [ ] **Copy files to new repository instead of using an existing one; meaning, don't put the history in the public repository**

## Future Considerations
* how to scan the repository
* how to deploy to scan for GFE that needs it (maybe available through self service catalog)
* need to layout tools - static code - did you use "x"?; dynamic - did you use "x"?
* consider a template repository - includes README, contributing, etc.
* how do you open source the code? consider 12Factor
* how do you manage updates to the code

## Nice to Have
- [ ] **Is a `CHANGELOG.md` present and does it contain structured, consistently formatted recent history?**
    - Template TBD
- [ ] **Are there unit tests?**
- [ ] **If applicable and possible, is it set up in Jenkins or CircleCI?**
- [ ] **Have multiple people reviewed the code?**
- [ ] **Are the API docs generated?**
