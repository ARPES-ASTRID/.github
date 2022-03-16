# About
This organization is for storing code used at the SGM3 beamline of ASTRID2 of the Aarhus University Physics and Astronomy Department, in Aarhus, Denmark.

# Usage
The Organization contains several Igor procedure repos.
A good workflow is to clone them directly in your User Procedures folder.

To clone all the Igor repos at once, you can follow these instructions (tested on Mac):
- Generate a Github [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
- install jq on your terminal to handle the json that the Github API returns
- in the terminal, navigate to your User Procedures folder ```~/Documents/WaveMetrics/Igor Pro <version number> User Files/User Procedures```
- clone all the Igor repos by executing
```
curl -s https://[token]:@api.github.com/orgs/arpes-astrid/repos\?per_page\=200  | jq '.[] | select(.description | contains("Igor"))' | jq ".ssh_url" | xargs -n 1 git clone --recursive)
```