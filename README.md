# Missing lookup values for children records


## Bug description

When importing children of lookup relationship, if first record in the child file has parent field empty, all child records are insert/updated to empty parent field.
## Plugins setup
- @oclif/plugin-autocomplete 0.3.0 (core)
- @oclif/plugin-commands 1.3.0 (core)
- @oclif/plugin-help 3.3.1 (core)
- @oclif/plugin-not-found 1.2.6 (core)
- @oclif/plugin-plugins 1.10.11 (core)
- @oclif/plugin-update 1.5.0 (core)
- @oclif/plugin-warn-if-update-available 1.7.3 (core)
- @oclif/plugin-which 1.0.4 (core)
- @salesforce/sfdx-plugin-lwc-test 0.1.7 (core)
- alias 2.0.0 (core)
- apex 0.11.0 (core)
- auth 2.0.2 (core)
- community 1.1.4 (core)
- config 1.4.6 (core)
- custom-metadata 1.1.0 (core)
- data 0.6.15 (core)
- generator 2.0.0 (core)
- info 2.0.0 (core)
- limits 2.0.0 (core)
- org 1.12.1 (core)
- salesforce-alm 54.3.0 (core)
- schema 2.1.0 (core)
- sfdmu 4.14.3
- sfdx-cli 7.150.0 (core)
- signups 1.0.0 (core)
- source 1.9.7 (core)
- telemetry 1.4.0 (core)
- templates 54.6.0 (core)
- trust 1.1.0 (core)
- user 1.7.1 (core)

## Prerequisites

- Create new, empty scratch org
## Working scenario
### Data

- Account: 1
- Opportunity: 2, first of them has Account assigned, second one has not.

![Case.csv](/images/working-cases-file.png)
### Command

- run command `sfdx sfdmu:run -s csvfile -u [your org name] -p .\data-working\`

### Result
- This inserts 1 Account and 2 Cases, of which 1 has Account related.
![Case List View](/images/working-cases-view.png)

## Failing scenario
### Data

- Account: 1
- Opportunity: 2, second of them has Account asigned, first one has not.

![Case.csv](/images/working-cases-file.png)
### Command
- run command `sfdx sfdmu:run -s csvfile -u [your org name] -p .\data-not-working\`
### Expected result

- This command inserts 1 Account and 2 Cases, of which 1 has Account related.

### Actuall result

- This inserts 1 Account and 2 Cases, but none has Account related.

![Case List View](/images/not-working-cases-view.png)

