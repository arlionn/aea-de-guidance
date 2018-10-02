## Suggested Information for Data
### Data description
-  Please describe all data, including input data.
- This is often called "metadata"
  - At a minimum, all variables that are used in the paper should be well-described (variable/column labels, value labels, summary statistics) through a codebook.
  - If confidentiality protection is a concern, talk to your data provider. You may be able to apply simple count and fraction rounding rules (see [code in this Github repository](https://github.com/simsong/drb_rounder)), or remove some summary statistics (e.g., max/min or specific quantiles).
-  Where multiple versions of the data exist, describe the version of the data used by the author.
  -  If possible, provide a Digital Object Identifier.
-  This information can be generated by the paper author, or provided by pointing to a URL of the data provider (for instance an online codebook).
- Some detailed guidance is available in the [DataONE Primer on Data Management Best Practices](http://www.dataone.org/sites/all/documents/DataONE_BP_Primer_020212.pdf). Other primers also exist.

### Practical guidance: Data description

It doesn't need to be complicated, but should be complete.

#### Stata

In Stata,the native 'codebook' command can generate such information:
```
// Stata
use my_input_data
describe
codebook
```
See [code/01_codebook_fancy.md](code/01_codebook_fancy.md) for a fancier example, and [code/02_codebook_plaintext.md](code/02_codebook_plaintext.md) for the code and output from the simpler example.

#### R

In R, the [dataMaid](https://cran.r-project.org/web/packages/dataMaid/index.html) [[1](http://sandsynligvis.dk/2017/08/21/datamaid-your-personal-assistant-for-cleaning-up-the-data-cleaning-process/)], [[2](http://sandsynligvis.dk/articles/18/codebook.html)] can accomplish a similar task:
```{r}
# use the    dataMaid   package
library(dataMaid)
makeCodebook(my_input_data)
```

#### More elaborate methods
However, if you have the ability to do a more robust data description, you should. See a [self-citing example](https://www2.ncrn.cornell.edu/ced2ar-web/codebooks/synlbd/v/v2).

### Data access description
The description of data access should provide enough information so that an uninformed user could theoretically access the data.
- This can be as simple as a download URL.
- It might be a pointer to a directory in the replication archive.
- This might also be the URL for a description of the application procedure (e.g. NCHS, https://www.cdc.gov/rdc/leftbrch/userestricdt.htm , or PSID https://simba.isr.umich.edu/restricted/ProcessReq.aspx), and an estimate of the monetary and time cost of the application process.
- Provide the date when the data access description was valid. For long-running projects, this may be the information when YOU accessed the data, or it may be the access information for somebody who wants to access the data TODAY.
- Provide information on the **access conditions**:
  - Does a downloader need to agree to simple terms of use? (Example: IPUMS-USA https://usa.ipums.org/usa/cite.shtml)
  - Does the researcher need to provide information (project proposal, computer security plan, etc.)? (Example: PSID https://simba.isr.umich.edu/U/CondUse.aspx)
  - Is there perhaps a residency or citizen requirement?

#### Practical guidance: data access
While non-academic data providers may not always consider reproducibility when you sign a contract with them, we have found numerous such providers which are open to at least the idea of "reproducibility checking" or replication. Examples of agreements which allow third-parties to access confidential data for the purpose of replication, see f.i. [supplementary materials](https://www.aeaweb.org/aer/data/oct2013/20110834_data.zip) to [Barseghyan et al (2013)](https://doi.org/10.1257/aer.103.6.2499).

### Data persistence
Data should remain available for a sufficiently long time.
-  By depositing in the **AEA Data and Code Repository**, the data (and code) will remain available indefinitely.
-  This is also true if the data is in various other repositories
-  This may also be true if the data cannot be shared (restricted access data).
-  A good minimum benchmark is 10 years, but this may not always be feasible with data the author does not control.
You should describe the data persistence, or point to a data archive's policy in that matter. See [Suggested_information_hosting](Suggested_information_hosting.md) for more details on data repositories.

### What is a data provider
A "data provider" in this sense can be a public repository where the data can be found ([ICPSR](https://www.icpsr.umich.edu/icpsrweb/)), a website that provided the data ([IPUMS](https://usa.ipums.org/usa/)), a statistical agency or private company that granted access to the data ([U.S. Census Bureau](https://www.census.gov/fsrdc), Twitter, Acme Inc.).
The author may also be the data provider, for instance, because the author conducted the survey used in the article. However, in many cases, the data provider may not be a data archive (see  [Suggested_information_hosting](Suggested_information_hosting.md)).

#### Practical guidance: data provider and data archives
If the data provider is not an archive (i.e., the data persistence is insufficient, and might go away), you should investigate depositing the data at a data archive.