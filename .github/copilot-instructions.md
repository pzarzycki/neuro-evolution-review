
 # Copilot instructions — Google Scholar first

 What I can do

 - When asked to research a scientific paper, start with Google Scholar (exact title + authors), then corroborate with arXiv, CrossRef/DOI, and canonical code repositories (GitHub/GitLab).

 How to ask

 - Provide the paper title and authors (preferred). Example: "Find canonical links and citation count for: 'Evolving Neural Networks through Augmenting Topologies' by Stanley and Miikkulainen (2002)."

 Rules (short)

 - Query Google Scholar first. If no clear GS match, fall back to arXiv, CrossRef, or OpenAlex and record which fallback was used.
 - Prefer open PDFs in this order: arXiv -> author-hosted -> publisher. Always record paywall status.
 - Locate canonical code repos and prefer organisation-maintained GitHub repos.

 Output contract (single JSON object)

 Return exactly one JSON object with these fields:
 - title (string)
 - authors (array of strings)
 - year (integer)
 - venue (string or null)
 - doi (string or null)
 - arxiv (string or null)
 - pdf (best open PDF URL or null)
 - gs_citations (integer or null)
 - gs_url (string or null)
 - publisher_url (string or null)
 - canonical_code_repo (string or null)
 - notes (short string)

 Example output

 {
   "title": "Evolving Neural Networks through Augmenting Topologies",
   "authors": ["Kenneth O. Stanley", "Risto Miikkulainen"],
   "year": 2002,
   "venue": "Evolutionary Computation",
   "doi": "10.1162/106365602320169811",
   "arxiv": null,
   "pdf": null,
   "gs_citations": 4897,
   "gs_url": "https://scholar.google.com/scholar?...",
   "publisher_url": "https://direct.mit.edu/evco/article/10/2/99/1123/...",
   "canonical_code_repo": "https://github.com/CodeReclaimers/neat-python",
   "notes": "Google Scholar checked; publisher PDF behind access controls; no arXiv preprint found."
 }

 Legal & operational notes

 - Do not attempt to bypass paywalls or authentication. Prefer CrossRef/OpenAlex/arXiv APIs over scraping Google Scholar when automation is required.
 - Record the fallback used in `notes` if Google Scholar cannot be accessed.

 Maintainers

 - Follow legal constraints and prefer API-first approaches. Document fallbacks.


 ## Research steps (succinct)

 1. Query Google Scholar with the paper title and authors. Prefer exact-match results.
 2. From the matched GS entry record: gs_url, gs_citations (integer), and any PDF links.
 3. If GS is unavailable or ambiguous, fall back to arXiv search, then CrossRef/OpenAlex.
 4. Confirm DOI/publisher page (CrossRef) and arXiv id (if present). Record paywalled status in notes.
 5. Search for a canonical code repository (GitHub, GitLab) via the paper/author pages.

 ## JSON output contract

 Return a single JSON object with these fields:
 - title (string)
 - authors (array of strings)
 - year (integer)
 - venue (string or null)
 - doi (string or null)
 - arxiv (string or null)
 - pdf (best open PDF URL or null)
 - gs_citations (integer or null)
 - gs_url (string or null)
 - publisher_url (string or null)
 - canonical_code_repo (string or null)
 - notes (short string)

 ## Example (informational only)

 {
   "title": "Evolving Neural Networks through Augmenting Topologies",
   "authors": ["Kenneth O. Stanley", "Risto Miikkulainen"],
   "year": 2002,
   "venue": "Evolutionary Computation",
   "doi": "10.1162/106365602320169811",
   "arxiv": null,
   "pdf": null,
   "gs_citations": 4897,
   "gs_url": "https://scholar.google.com/scholar?...",
   "publisher_url": "https://direct.mit.edu/evco/article/10/2/99/1123/...",
   "canonical_code_repo": "https://github.com/CodeReclaimers/neat-python",
   "notes": "Google Scholar checked; publisher PDF behind access controls; no arXiv preprint found."
 }
