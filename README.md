
# Top DSpace Contributors

This GitHub Pages site lists the top [DSpace GitHub](https://github.com/DSpace) contributors *per month*. 

## How are the Top Contributors calculated / counted?

### General Notes
These statistics are ONLY gathered for activities within the [DSpace organization in GitHub](https://github.com/DSpace).  This means that all statistics are an aggregate from all projects under that organization, but they do NOT include activities in [DSpace-Labs](https://github.com/DSpace-Labs) or other organizations.

### Top PR Creators (per month)

The list of Top Pull Request creators is calculated based on the following:
* Pull Request MUST be created under a [DSpace GitHub](https://github.com/DSpace) project.
* Pull Request MUST be created in that given month. Updates/changes to older PRs during that month are not considered.
* Pull Request MUST be in the "open" or "merged" state. At this time, we do NOT count "closed" PRs, as it is assumed they were invalid and/or replaced by a different PR.
* Pull Requests are only credited based on the *author* of the PR.  We do not check for author(s) of individual commits.

For the exact calculations, see the [recent-pr-creators.sh](https://github.com/tdonohue/top-contributors/blob/master/scripts/recent-pr-creators.sh) script, and the [Where do these statistics come from?](#Where do these statistics come from?) section below.

### Top PR Reviewers (per month)

The list of Top Pull Request reviewrs is calculated based on the following:
* The Review MUST be on a Pull Request created under a [DSpace GitHub](https://github.com/DSpace) project.
* The Review MUST be a [GitHub Pull Request Review](https://help.github.com/articles/about-pull-request-reviews/). General comments on PRs are NOT included in the count.
* The Review MUST be created in that given month. 
* Reviews are counted regardless of the status of the Pull Request (even if the PR is now "closed", your review is counted).
* Only one review per Pull Request is counted. It is possible to submit multiple reviews per PR, but we are only counting the number of Pull Requests you have reviewed and NOT the number of reviews submitted. 

## Where do these statistics come from? 

The statistical results are gathered and compiled using two primary tools:
1. [GitHub GraphQL API](https://developer.github.com/v4/) is used to gather a list of *all* contribution types (e.g. PR creation or PR reviews) within a given date range. The result is a JSON document. If more than one page of results is found to exist, all results are compiled (appended) into a single, locally stored JSON output document.
   * https://developer.github.com/v4/explorer/ provides a way to test GitHub GraphQL syntax/queries online.
2. [jq (json parser)](https://stedolan.github.io/jq/) is used (from the commandline) to parse/sort/group the actual statistics from the JSON output document. So, `jq` does the heavy lifting of taking a list of contributions and grouping them by individual, counting them, and sorting based on that count. The result is a CSV output document which contains the "top contributors" based on a specific JSON input document.
    * https://jqplay.org/ provides a way to test `jq` syntax/queries online.
3. Finally, [GitHub Pages](https://pages.github.com/) is used to display the CSV output
    * The CSV output is uploaded as a [Jekyll Data File](https://jekyllrb.com/docs/datafiles/) (under `_data/[YYYY-MM]/*.csv`)
    * A new Jekyll blog post is created (under `_posts`) which uses the data file to create an HTML table of output.
    * Each blog post uses the same template to translate the CSV contents into an HTML table (and give out the "awards", which are just emoji). This template makes heavy use of the [Liquid templating language](https://shopify.github.io/liquid/) (used by Jekyll). See the [`pr-awards-table.html` template](https://github.com/tdonohue/top-contributors/blob/master/_includes/pr-awards-table.html)
    
The statistical scripts are available in this GitHub repository in the `scripts/` folder. They are Bash scripts that call GitHub GraphQL API (using `curl`), save the results to a local JSON file, and then parse that JSON file using `jq`, saving the final results in CSV.

### Running the scripts

The scripts that compile these statistics are available in `scripts/` folder. They can be run from the commandline (in Windows or Linux).

1. [Download and install jq](https://stedolan.github.io/jq/) on your system.  It comes packaged as a binary, so simply download it to a location on your harddrive.
2. Ensure Bash (or Git Bash on Windows) is installed on your system. You'll also need `curl`
3. Update the `script/*.sh` files, ensuring these variables are filled out:
    * `GITHUB_TOKEN` : must be set to your own, personal GitHub access token (required for access to GitHub GraphQL). See https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/
    * `JQ_EXEC` : the path / name of the `jq` script on your system. This can be a relative or absolute path.
    * `START_DATE` : specify the starting date for the statistics you wish to gather
    * `END_DATE`  : specify the end date for the statistics you wish to gather. Keep in mind that the date range should likely only be *one month* at a maximum. Larger ranges may not work properly, as GitHub GraphQL only returns a limited number of total results
    * `OUTPUT_JSON` : Optionally, change the name of the JSON output file (this is the raw JSON output from GitHub GraphQL)
    * `OUTPUT_CSV` : Optionally, change the name of the final CSV output file (this is the final statistics, calculated via `jq` from the raw JSON output).
3. Run the script, e.g. `./[script].sh`.
    * On Windows, scripts must be run by passing them to `sh`, e.g. `sh ./[script].sh`

## Testing this GitHub Pages site locally

1. Install the [Jekyll](https://jekyllrb.com/) gem
2. Install the `github-pages` gem. 
    * Here's a good guide: https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/
3. Clone this repo
4. Run `jekyll serve`
