# Search Optimization Framework

*Created: 2025-02-26T05:58:00Z*  
*Last Modified: 2025-02-26T05:58:00Z*  
*Version: 1.0*

## Overview

The Search Optimization Framework provides structured approaches to formulating more effective search queries, interpreting results, and integrating search capabilities with other AI functions. This guide establishes patterns for maximizing the value of information retrieval through search capabilities.

## Core Search Strategy

### 1. Query Formulation

The effectiveness of search begins with proper query construction:

#### General Query Construction Principles

1. **Specificity**: Include specific terms that narrow the search space
2. **Context**: Include relevant context to disambiguate terms
3. **Precision**: Use exact terminology when domain-specific knowledge is available
4. **Recency**: Include time qualifiers when temporal relevance matters
5. **Source Awareness**: Format queries to target authoritative sources

#### Query Templates

**General Information**:
```
{topic} {key aspect} {optional: time period}
```

**Specific Facts**:
```
{entity} {attribute} {optional: qualifier}
```

**Comparative Information**:
```
{entity1} vs {entity2} {comparison aspect}
```

**Problem-Solution**:
```
{problem statement} solution {optional: context}
```

**Tutorial/How-to**:
```
how to {action} {subject} {optional: context}
```

#### Example Query Transformations

| Initial Query | Optimized Query | Improvement |
|---------------|-----------------|-------------|
| "climate change" | "latest climate change research findings 2024" | Added recency and specificity |
| "javascript error" | "how to fix 'uncaught TypeError' in javascript promises" | Added error specificity and context |
| "best phone" | "comparison iPhone 15 vs Samsung S23 battery life performance" | Added specific devices and comparison aspect |
| "Python code" | "Python code example parsing JSON nested structures" | Added specific programming task |
| "medication side effects" | "atorvastatin common side effects clinical studies" | Added specific medication and authoritative source hint |

### 2. Result Interpretation

Structured approach to interpreting search results:

#### Source Evaluation Framework

1. **Authority**: Assess the expertise and credentials of the source
   - Academic institutions (.edu domains)
   - Government agencies (.gov domains)
   - Established organizations in the field
   - Recognized experts with credentials

2. **Recency**: Evaluate the timeliness of the information
   - Publication date prominently displayed
   - Content discusses recent developments
   - References to current research or data
   - No outdated recommendations or statistics

3. **Relevance**: Determine alignment with the query intent
   - Directly addresses the core question
   - Covers the specific aspect of interest
   - Provides the appropriate depth of information
   - Contextually appropriate to the domain

4. **Comprehensiveness**: Assess the depth and breadth of coverage
   - Multiple perspectives considered
   - Thorough explanation of concepts
   - Supporting evidence and examples
   - Coverage of limitations or exceptions

5. **Bias Assessment**: Identify potential biases or conflicts of interest
   - Balanced presentation of information
   - Transparent about funding or affiliations
   - Separates facts from opinions
   - Acknowledges limitations or contrary evidence

#### Information Extraction Template

For each valuable search result, extract and structure the information:

```
Source: [Website/Organization name] ([Domain type])
Date: [Publication or last updated date]
Key Points:
- [Main point 1]
- [Main point 2]
- [Main point 3]
Evidence Quality:
- [Type of evidence provided: statistics, studies, expert opinions, etc.]
- [Indicators of reliability or limitations]
Relevance: [High/Medium/Low] - [Brief justification]
```

### 3. Search Refinement Loops

Iterative process for improving search results:

#### Refinement Decision Tree

```
Start with initial query
│
├── If too many results → Add specificity
│   ├── Add domain-specific terminology
│   ├── Add qualifying criteria
│   └── Narrow time frame
│
├── If too few results → Broaden query
│   ├── Use more general terminology
│   ├── Remove overly specific qualifiers
│   └── Consider synonyms or related concepts
│
├── If results are off-topic → Redirect query
│   ├── Identify misinterpreted terms
│   ├── Use different terminology
│   └── Add clarifying context
│
└── If results lack authority → Add source indicators
    ├── Add "research" or "studies"
    ├── Add "official" or "government"
    └── Target specific authoritative domains
```

#### Refinement Examples

| Initial Query | Feedback | Refined Query |
|---------------|----------|---------------|
| "machine learning algorithms" | Too broad | "comparison of gradient boosting algorithms for time series prediction" |
| "CRISPR cancer treatment" | Too specific/few results | "gene editing approaches for cancer therapy research" |
| "apple productivity apps" | Ambiguous (fruit vs. company) | "Apple iOS productivity applications for project management" |
| "diet advice" | Low authority results | "dietary guidelines American Heart Association" |
| "covid vaccine" | Outdated information | "covid vaccine effectiveness against variants 2024 studies" |

## Integration with Other Capabilities

### Search + Sequential Thinking

Combine search with sequential thinking for research-driven reasoning:

#### Research-Then-Reason Pattern

1. **Initial Thought**: Formulate the research question
   ```
   thoughtNumber: 1,
   thought: "To analyze the impact of remote work on productivity, I need current research findings. Let me search for this information.",
   nextThoughtNeeded: true
   ```

2. **Search Integration**: Use search to gather evidence
   ```
   query: "impact of remote work on productivity research studies 2023-2024"
   ```

3. **Evidence Processing**: Analyze and synthesize search results
   ```
   thoughtNumber: 2,
   thought: "Based on the search results, I found several key insights: 1) A Stanford study showed a 13% productivity increase from remote work, attributed to fewer breaks and quieter work environments. 2) However, a Harvard Business Review article noted collaboration and innovation may suffer in fully remote settings. 3) The most recent research indicates hybrid models optimize both individual productivity and team collaboration.",
   nextThoughtNeeded: true
   ```

4. **Reasoning with Evidence**: Develop conclusions based on evidence
   ```
   thoughtNumber: 3,
   thought: "Synthesizing this research, the impact of remote work on productivity appears context-dependent. Individual productivity metrics often improve with remote work due to fewer interruptions and commute elimination. However, collaborative productivity and innovation may decline without in-person interaction. This suggests that the optimal approach for most organizations would be a hybrid model that balances these factors.",
   nextThoughtNeeded: false
   ```

#### Knowledge Gap Identification Pattern

1. **Initial Analysis**: Identify knowledge gaps
   ```
   thoughtNumber: 1,
   thought: "To evaluate this ML model architecture, I need to understand the latest approaches to preventing overfitting in transformer-based models. There seems to be a knowledge gap here.",
   nextThoughtNeeded: true
   ```

2. **Targeted Search**: Search for specific missing information
   ```
   query: "transformer models overfitting prevention techniques research"
   ```

3. **Knowledge Integration**: Incorporate new information
   ```
   thoughtNumber: 2,
   thought: "The search revealed several techniques for preventing overfitting in transformer models: 1) Stochastic depth - randomly dropping layers during training, 2) LayerDrop - a structured form of dropout specific to transformers, 3) Weight decay augmented with specific regularization terms for attention mechanisms, and 4) Data augmentation techniques specific to the input modality.",
   nextThoughtNeeded: true
   ```

4. **Enhanced Analysis**: Continue reasoning with new knowledge
   ```
   thoughtNumber: 3,
   thought: "With this information, I can now evaluate the model architecture more effectively. The model uses basic dropout but could benefit from implementing stochastic depth, which the research shows is particularly effective for large transformer models. Additionally, the custom regularization approach for attention weights mentioned in the Zhang et al. paper would address the specific overfitting issues observed in the attention maps.",
   nextThoughtNeeded: false
   ```

### Search + Knowledge Graph

Use search to enhance and validate knowledge graph content:

#### Knowledge Enrichment Pattern

1. **Identify Knowledge Gaps**: Detect missing information in knowledge graph
   ```javascript
   // Analyze entity for missing information
   function identifyKnowledgeGaps(entityName) {
     const entity = getEntity(entityName);
     const observations = entity.observations;
     
     // Check for key attributes based on entity type
     const gaps = [];
     if (entity.entityType === "Person" && !observations.some(o => o.includes("birth date"))) {
       gaps.push("birth date");
     }
     if (entity.entityType === "Organization" && !observations.some(o => o.includes("founded"))) {
       gaps.push("founding date");
     }
     // More gap identification logic...
     
     return gaps;
   }
   ```

2. **Search for Missing Information**: Formulate targeted search queries
   ```javascript
   // Generate search queries for knowledge gaps
   function generateGapQueries(entityName, gaps) {
     const entity = getEntity(entityName);
     
     return gaps.map(gap => ({
       gap,
       query: `${entityName} ${gap}`
     }));
   }
   ```

3. **Update Knowledge Graph**: Integrate search results into knowledge graph
   ```javascript
   // Update knowledge graph with search results
   async function enrichEntityWithSearch(entityName, gaps) {
     const queries = generateGapQueries(entityName, gaps);
     
     for (const {gap, query} of queries) {
       // Search for information
       const searchResults = await braveWebSearch({query});
       
       // Extract relevant information
       const extracted = extractInformationForGap(searchResults, gap);
       
       if (extracted) {
         // Add new observation to entity
         await addObservations({
           observations: [{
             entityName,
             contents: [`${gap}: ${extracted}`]
           }]
         });
         
         console.log(`Updated entity ${entityName} with ${gap}`);
       }
     }
   }
   ```

#### Fact Verification Pattern

1. **Identify Claims to Verify**: Extract factual claims from knowledge graph
   ```javascript
   // Extract factual claims from entity
   function extractVerifiableClaims(entityName) {
     const entity = getEntity(entityName);
     const observations = entity.observations;
     
     // Filter for observations that appear to be factual claims
     return observations.filter(obs => 
       !obs.includes("opinion") && 
       !obs.includes("might") && 
       !obs.includes("may") &&
       !obs.startsWith("Created:") &&
       !obs.startsWith("Modified:")
     );
   }
   ```

2. **Search for Verification**: Generate verification queries
   ```javascript
   // Generate verification queries for claims
   function generateVerificationQueries(entityName, claims) {
     return claims.map(claim => ({
       claim,
       query: `${entityName} ${claim} fact check`
     }));
   }
   ```

3. **Update Confidence Levels**: Adjust knowledge confidence based on verification
   ```javascript
   // Update confidence based on verification
   async function verifyClaimsWithSearch(entityName, claims) {
     const queries = generateVerificationQueries(entityName, claims);
     const verificationResults = [];
     
     for (const {claim, query} of queries) {
       // Search for verification
       const searchResults = await braveWebSearch({query});
       
       // Assess verification level
       const verification = assessVerification(searchResults, claim);
       
       verificationResults.push({
         claim,
         verificationLevel: verification.level,
         sources: verification.sources
       });
       
       // Update original observation with confidence
       await addObservations({
         observations: [{
           entityName,
           contents: [`Verification for "${claim}": ${verification.level} (Sources: ${verification.sources.join(", ")})`]
         }]
       });
     }
     
     return verificationResults;
   }
   ```

### Search + GitHub Integration

Use search to enhance code-related queries and implementation:

#### Implementation Research Pattern

1. **Problem Understanding**: Define the coding challenge
   ```
   thoughtNumber: 1,
   thought: "I need to implement a high-performance bloom filter in Python. Let me first understand the best approaches and existing implementations.",
   nextThoughtNeeded: true
   ```

2. **General Search**: Research the topic broadly
   ```
   query: "high performance bloom filter implementation python"
   ```

3. **GitHub-Specific Search**: Find actual implementations
   ```javascript
   // Search for repositories with bloom filter implementations
   const repoResults = await searchRepositories({
     query: "bloom filter python stars:>50"
   });
   
   // Search for specific code implementations
   const codeResults = await searchCode({
     q: "function bloom filter python language:python"
   });
   ```

4. **Implementation Synthesis**: Combine findings into a solution
   ```
   thoughtNumber: 2,
   thought: "From the search results and GitHub code analysis, I've found that the most efficient Python bloom filter implementations use 'bitarray' for storage and implement double hashing with a bit-shifting approach. The pybloom_live package seems well-maintained, but for our specific needs, we should implement a custom solution with the following characteristics...",
   nextThoughtNeeded: true
   ```

5. **Implementation with Attribution**: Create code with proper attribution
   ```python
   """
   High-performance Bloom Filter implementation in Python.
   
   Based on research from:
   1. 'Bloom Filters in Python: A Practical Guide' (found via web search)
   2. GitHub repository pybloom_live implementation patterns
   3. 'Optimal Hash Functions for Bloom Filters' research paper
   
   Created: 2025-02-26T05:58:00Z
   """
   import math
   import mmh3
   from bitarray import bitarray
   
   class BloomFilter:
       def __init__(self, capacity, error_rate=0.001):
           """Initialize a Bloom Filter.
           
           Args:
               capacity: Expected number of elements to be added
               error_rate: Desired false positive rate
           """
           # Calculate optimal filter size and number of hash functions
           self.size = self._calculate_size(capacity, error_rate)
           self.hash_count = self._calculate_hash_count(self.size, capacity)
           
           # Initialize bitarray
           self.bit_array = bitarray(self.size)
           self.bit_array.setall(0)
           
           self.capacity = capacity
           self.error_rate = error_rate
           self.count = 0
           
       def _calculate_size(self, capacity, error_rate):
           """Calculate optimal bit array size."""
           m = -capacity * math.log(error_rate) / (math.log(2) ** 2)
           return int(m)
       
       def _calculate_hash_count(self, size, capacity):
           """Calculate optimal number of hash functions."""
           k = (size / capacity) * math.log(2)
           return int(k)
       
       def add(self, item):
           """Add an item to the Bloom filter."""
           for seed in range(self.hash_count):
               index = mmh3.hash(str(item), seed) % self.size
               self.bit_array[index] = 1
           
           self.count += 1
       
       def contains(self, item):
           """Check if item might be in the Bloom filter.
           
           Returns:
               bool: True if item might be present, False if definitely not present
           """
           for seed in range(self.hash_count):
               index = mmh3.hash(str(item), seed) % self.size
               if not self.bit_array[index]:
                   return False
           return True
       
       def current_false_positive_rate(self):
           """Calculate current false positive probability based on fill level."""
           if self.count == 0:
               return 0.0
           
           fill_ratio = self.count / self.capacity
           return (1 - math.exp(-self.hash_count * fill_ratio)) ** self.hash_count
   ```

## Search Implementation Patterns

### Effective Query Construction

```javascript
/**
 * Generate an optimized search query from a user question
 * 
 * @param {string} userQuestion - Original user question
 * @param {Object} options - Query configuration options
 * @returns {string} Optimized search query
 */
function generateOptimizedQuery(userQuestion, options = {}) {
  // Extract key concepts using NLP techniques
  const keyConcepts = extractKeyConcepts(userQuestion);
  
  // Remove unnecessary words
  const filteredConcepts = keyConcepts.filter(concept => 
    !['how', 'what', 'when', 'where', 'why', 'is', 'are', 'the'].includes(concept.toLowerCase())
  );
  
  // Add context terms if available
  let queryTerms = [...filteredConcepts];
  if (options.context) {
    queryTerms.push(options.context);
  }
  
  // Add recency if temporal relevance matters
  if (options.recencyMatters) {
    const currentYear = new Date().getFullYear();
    queryTerms.push(currentYear.toString());
  }
  
  // Add source quality indicators if specified
  if (options.preferAcademic) {
    queryTerms.push('research studies');
  } else if (options.preferOfficial) {
    queryTerms.push('official');
  }
  
  // Construct the final query
  let query = queryTerms.join(' ');
  
  // Add explicit domain restrictions if needed
  if (options.domainRestrictions && options.domainRestrictions.length > 0) {
    query += ' site:' + options.domainRestrictions.join(' OR site:');
  }
  
  return query;
}

/**
 * Extract key concepts from a user question
 * This is a simplified implementation - would use proper NLP in production
 */
function extractKeyConcepts(userQuestion) {
  // Remove punctuation and split into words
  const words = userQuestion.replace(/[.,\/#!$%\^&\*;:{}=\-_`~()]/g, "").split(/\s+/);
  
  // Remove common stop words (simplified)
  const stopWords = ['a', 'an', 'the', 'is', 'are', 'was', 'were', 'be', 'been', 'being',
                    'in', 'on', 'at', 'to', 'for', 'with', 'about', 'against', 'between',
                    'into', 'through', 'during', 'before', 'after', 'above', 'below',
                    'from', 'up', 'down', 'of', 'and', 'but', 'or', 'so', 'than', 'that'];
  
  const concepts = words.filter(word => 
    word.length > 1 && !stopWords.includes(word.toLowerCase())
  );
  
  // Find multi-word concepts (simplified)
  const multiWordConcepts = [];
  for (let i = 0; i < words.length - 1; i++) {
    if (!stopWords.includes(words[i].toLowerCase()) && 
        !stopWords.includes(words[i+1].toLowerCase())) {
      multiWordConcepts.push(`${words[i]} ${words[i+1]}`);
    }
  }
  
  // Combine single words and multi-word concepts
  return [...new Set([...concepts, ...multiWordConcepts])];
}
```

### Result Processing and Ranking

```javascript
/**
 * Process and rank search results based on relevance and authority
 * 
 * @param {Array} searchResults - Raw search results
 * @param {string} originalQuery - The original search query
 * @param {Object} options - Processing options
 * @returns {Array} Processed and ranked results
 */
function processSearchResults(searchResults, originalQuery, options = {}) {
  if (!searchResults || searchResults.length === 0) {
    return [];
  }
  
  // Extract query terms for relevance scoring
  const queryTerms = originalQuery.toLowerCase().split(/\s+/);
  
  // Process each result
  const processedResults = searchResults.map(result => {
    // Calculate relevance score
    const titleRelevance = calculateRelevance(result.title, queryTerms);
    const snippetRelevance = calculateRelevance(result.snippet, queryTerms);
    
    // Calculate authority score
    const authorityScore = calculateAuthorityScore(result.url);
    
    // Calculate recency score if applicable
    const recencyScore = options.considerRecency 
      ? calculateRecencyScore(result.published_date) 
      : 0;
    
    // Calculate overall score (weighted combination)
    const overallScore = (
      (titleRelevance * 0.4) + 
      (snippetRelevance * 0.3) + 
      (authorityScore * 0.2) + 
      (recencyScore * 0.1)
    );
    
    return {
      ...result,
      scores: {
        relevance: (titleRelevance + snippetRelevance) / 2,
        authority: authorityScore,
        recency: recencyScore,
        overall: overallScore
      },
      processed: {
        keyPoints: extractKeyPoints(result.snippet),
        entities: extractEntities(result.title + " " + result.snippet),
        domainType: getDomainType(result.url)
      }
    };
  });
  
  // Rank results by overall score
  const rankedResults = processedResults.sort((a, b) => 
    b.scores.overall - a.scores.overall
  );
  
  return rankedResults;
}

/**
 * Calculate relevance score based on term matching
 */
function calculateRelevance(text, queryTerms) {
  if (!text) return 0;
  
  const normalizedText = text.toLowerCase();
  
  // Count how many query terms appear in the text
  const matchedTerms = queryTerms.filter(term => 
    normalizedText.includes(term)
  );
  
  const termMatchRatio = matchedTerms.length / queryTerms.length;
  
  // Consider exact phrase matches
  const exactPhraseMatch = normalizedText.includes(queryTerms.join(' '));
  const exactMatchBonus = exactPhraseMatch ? 0.3 : 0;
  
  // Consider term proximity (simplified)
  const proximityScore = calculateTermProximity(normalizedText, queryTerms);
  
  return Math.min(1, termMatchRatio + exactMatchBonus + proximityScore);
}

/**
 * Calculate term proximity score (simplified)
 */
function calculateTermProximity(text, queryTerms) {
  // Simplified implementation
  if (queryTerms.length < 2) return 0;
  
  let foundAllTerms = true;
  for (const term of queryTerms) {
    if (!text.includes(term)) {
      foundAllTerms = false;
      break;
    }
  }
  
  return foundAllTerms ? 0.2 : 0;
}

/**
 * Calculate authority score based on URL
 */
function calculateAuthorityScore(url) {
  if (!url) return 0;
  
  // Check for top-level domain indicators of authority
  if (url.includes('.gov') || url.includes('.mil')) {
    return 0.9; // Government/military domains
  } else if (url.includes('.edu')) {
    return 0.8; // Educational institutions
  } else if (url.includes('.org')) {
    return 0.7; // Non-profit organizations
  }
  
  // Check for known high-authority domains (simplified list)
  const authorityDomains = [
    'wikipedia.org',
    'who.int',
    'nih.gov',
    'nature.com',
    'science.org',
    'ieee.org',
    'acm.org',
    'britannica.com'
  ];
  
  for (const domain of authorityDomains) {
    if (url.includes(domain)) {
      return 0.85;
    }
  }
  
  // Default score for other domains
  return 0.5;
}

/**
 * Calculate recency score based on publication date
 */
function calculateRecencyScore(publishedDate) {
  if (!publishedDate) return 0;
  
  const now = new Date();
  const published = new Date(publishedDate);
  
  // Invalid date
  if (isNaN(published.getTime())) {
    return 0;
  }
  
  // Calculate age in days
  const ageInDays = (now - published) / (1000 * 60 * 60 * 24);
  
  // Recency scoring logic:
  // - Content less than 7 days old: 0.9-1.0
  // - Content less than 30 days old: 0.7-0.9
  // - Content less than 90 days old: 0.5-0.7
  // - Content less than 365 days old: 0.3-0.5
  // - Content older than 365 days: 0.0-0.3
  
  if (ageInDays < 7) {
    return 0.9 + (7 - ageInDays) / 70;
  } else if (ageInDays < 30) {
    return 0.7 + (30 - ageInDays) / 150;
  } else if (ageInDays < 90) {
    return 0.5 + (90 - ageInDays) / 300;
  } else if (ageInDays < 365) {
    return 0.3 + (365 - ageInDays) / 1095;
  } else {
    return Math.max(0, 0.3 - (ageInDays - 365) / 3650);
  }
}

/**
 * Extract key points from text (simplified)
 */
function extractKeyPoints(text) {
  if (!text) return [];
  
  // Simple sentence splitting
  const sentences = text.split(/[.!?]/).filter(s => s.trim().length > 0);
  
  // Filter for sentences that appear to contain key information
  return sentences.filter(sentence => 
    // Sentences with numbers often contain key statistics
    /\d+/.test(sentence) ||
    // Sentences with key indicator phrases
    /important|significant|critical|essential|key|main|primary|found|discovered|revealed|suggests/i.test(sentence)
  ).map(s => s.trim());
}

/**
 * Extract entities from text (simplified)
 */
function extractEntities(text) {
  if (!text) return [];
  
  // Very simplified entity extraction - would use proper NLP in production
  // Look for capitalized multi-word phrases
  const entityRegex = /\b([A-Z][a-z]+ )+[A-Z][a-z]+\b/g;
  return [...new Set(text.match(entityRegex) || [])];
}

/**
 * Get domain type from URL
 */
function getDomainType(url) {
  if (!url) return 'unknown';
  
  if (url.includes('.gov')) return 'government';
  if (url.includes('.edu')) return 'education';
  if (url.includes('.org')) return 'organization';
  if (url.includes('.mil')) return 'military';
  if (url.includes('.com')) return 'commercial';
  if (url.includes('.net')) return 'network';
  if (url.includes('.io')) return 'technology';
  
  return 'other';
}
```

### Search Chain Orchestration

```javascript
/**
 * Execute a multi-stage search process to answer a complex question
 * 
 * @param {string} userQuestion - Original question from user
 * @returns {Object} Comprehensive answer with sources
 */
async function orchestratedSearch(userQuestion) {
  // Stage 1: Initial broad search
  const initialQuery = generateOptimizedQuery(userQuestion, {
    recencyMatters: true
  });
  
  const initialResults = await braveWebSearch({
    query: initialQuery,
    count: 5
  });
  
  // Process initial results
  const processedInitialResults = processSearchResults(
    initialResults.web.results,
    initialQuery,
    { considerRecency: true }
  );
  
  // Stage 2: Extract key concepts for focused searches
  const extractedConcepts = extractConceptsFromResults(processedInitialResults);
  
  // Generate focused queries
  const focusedQueries = generateFocusedQueries(userQuestion, extractedConcepts);
  
  // Stage 3: Execute focused searches
  const focusedSearchResults = await Promise.all(
    focusedQueries.map(query => 
      braveWebSearch({
        query: query,
        count: 3
      })
    )
  );
  
  // Process focused results
  const processedFocusedResults = focusedSearchResults.flatMap((result, index) =>
    processSearchResults(
      result.web.results, 
      focusedQueries[index],
      { considerRecency: true }
    )
  );
  
  // Stage 4: Synthesize comprehensive answer
  return synthesizeAnswer(
    userQuestion,
    processedInitialResults,
    processedFocusedResults,
    extractedConcepts
  );
}

/**
 * Extract key concepts from search results
 */
function extractConceptsFromResults(results) {
  // Collect all entities and potential concepts
  const allEntities = results.flatMap(result => result.processed.entities);
  
  // Count entity frequency
  const entityCounts = allEntities.reduce((counts, entity) => {
    counts[entity] = (counts[entity] || 0) + 1;
    return counts;
  }, {});
  
  // Select top entities by frequency
  const topEntities = Object.entries(entityCounts)
    .sort((a, b) => b[1] - a[1])
    .slice(0, 5)
    .map(entry => entry[0]);
  
  // Extract additional key terms from result titles and snippets
  const keyTerms = extractKeyTermsFromResults(results);
  
  return {
    entities: topEntities,
    terms: keyTerms
  };
}

/**
 * Extract key terms from result titles and snippets
 */
function extractKeyTermsFromResults(results) {
  // Combine all titles and snippets
  const allText = results.map(r => 
    `${r.title} ${r.snippet}`
  ).join(' ');
  
  // Simple word frequency analysis (would use proper NLP in production)
  const words = allText.toLowerCase().match(/\b[a-z]{4,}\b/g) || [];
  
  // Count word frequency
  const wordCounts = words.reduce((counts, word) => {
    counts[word] = (counts[word] || 0) + 1;
    return counts;
  }, {});
  
  // Remove common stop words
  const stopWords = ['with', 'this', 'that', 'from', 'they', 'have', 'more', 'their', 'about'];
  for (const word of stopWords) {
    delete wordCounts[word];
  }
  
  // Select top terms by frequency
  return Object.entries(wordCounts)
    .sort((a, b) => b[1] - a[1])
    .slice(0, 10)
    .map(entry => entry[0]);
}

/**
 * Generate focused queries based on initial results
 */
function generateFocusedQueries(userQuestion, concepts) {
  const queries = [];
  
  // Entity-focused queries
  for (const entity of concepts.entities.slice(0, 3)) {
    queries.push(`${entity} ${userQuestion}`);
  }
  
  // Specific aspect queries using key terms
  if (concepts.terms.length >= 2) {
    queries.push(`${concepts.terms[0]} ${concepts.terms[1]} ${userQuestion}`);
  }
  
  // Add a query focused on latest research/information
  queries.push(`latest research ${userQuestion} ${new Date().getFullYear()}`);
  
  return queries;
}

/**
 * Synthesize a comprehensive answer from search results
 */
function synthesizeAnswer(question, initialResults, focusedResults, concepts) {
  // Combine and deduplicate results
  const allResults = [...initialResults];
  
  // Add focused results only if they're not duplicates of initial results
  for (const result of focusedResults) {
    if (!allResults.some(r => r.url === result.url)) {
      allResults.push(result);
    }
  }
  
  // Sort by overall score
  const sortedResults = allResults.sort((a, b) => 
    b.scores.overall - a.scores.overall
  );
  
  // Extract key information
  const keyPoints = sortedResults.flatMap(result => 
    result.processed.keyPoints.slice(0, 2)
  );
  
  // Deduplicate key points (simplified)
  const uniqueKeyPoints = [...new Set(keyPoints)];
  
  // Group sources by domain type
  const sourcesByType = sortedResults.reduce((grouped, result) => {
    const type = result.processed.domainType;
    if (!grouped[type]) {
      grouped[type] = [];
    }
    grouped[type].push({
      title: result.title,
      url: result.url,
      score: result.scores.overall
    });
    return grouped;
  }, {});
  
  // Construct the answer
  return {
    question,
    summary: generateSummary(uniqueKeyPoints, question, concepts),
    keyPoints: uniqueKeyPoints.slice(0, 10),
    sources: {
      primary: sortedResults.slice(0, 3).map(r => ({
        title: r.title,
        url: r.url,
        domainType: r.processed.domainType,
        relevance: r.scores.relevance
      })),
      byType: sourcesByType
    },
    concepts: {
      entities: concepts.entities,
      keyTerms: concepts.terms
    },
    searchProcess: {
      initialQuery: generateOptimizedQuery(question, { recencyMatters: true }),
      focusedQueries: generateFocusedQueries(question, concepts),
      resultCount: sortedResults.length
    }
  };
}

/**
 * Generate a concise summary from key points
 */
function generateSummary(keyPoints, question, concepts) {
  // This would use more sophisticated summarization in production
  // Here we're using a simple approach of combining top key points
  
  // Limit to first 5 key points
  const limitedPoints = keyPoints.slice(0, 5);
  
  // Join with transition phrases
  const combinedPoints = limitedPoints.join(' Furthermore, ');
  
  // Add introduction
  const introduction = `Based on search results about ${question}, the key findings include: `;
  
  // Add concepts when relevant
  let conceptsPhrase = '';
  if (concepts.entities.length > 0) {
    conceptsPhrase = ` The most relevant entities include ${concepts.entities.slice(0, 3).join(', ')}.`;
  }
  
  return introduction + combinedPoints + conceptsPhrase;
}
```

### Local Search Optimization

```javascript
/**
 * Generate optimized local search query
 * 
 * @param {string} userQuery - Original user query
 * @param {Object} locationContext - Location information
 * @returns {string} Optimized local search query
 */
function generateLocalSearchQuery(userQuery, locationContext = null) {
  // Extract business type and qualifiers
  const { businessType, qualifiers } = extractBusinessIntent(userQuery);
  
  // Check if query already contains location information
  const hasLocationInQuery = checkLocationInQuery(userQuery);
  
  // Build optimized query
  let optimizedQuery = businessType;
  
  // Add qualifiers if present
  if (qualifiers.length > 0) {
    optimizedQuery += ` ${qualifiers.join(' ')}`;
  }
  
  // Add location if not in query but available in context
  if (!hasLocationInQuery && locationContext) {
    let locationString = '';
    
    if (locationContext.city && locationContext.state) {
      locationString = `${locationContext.city}, ${locationContext.state}`;
    } else if (locationContext.city) {
      locationString = locationContext.city;
    } else if (locationContext.state) {
      locationString = locationContext.state;
    } else if (locationContext.coordinates) {
      // Just use "near me" if we have coordinates but no named location
      locationString = "near me";
    }
    
    if (locationString) {
      optimizedQuery += ` in ${locationString}`;
    }
  }
  
  return optimizedQuery;
}

/**
 * Extract business intent from query
 */
function extractBusinessIntent(query) {
  // List of common business types
  const businessTypes = [
    'restaurant', 'cafe', 'coffee shop', 'bar', 'pub', 'hotel', 'motel',
    'store', 'shop', 'mall', 'salon', 'spa', 'gym', 'fitness center',
    'doctor', 'dentist', 'hospital', 'clinic', 'pharmacy', 'school',
    'university', 'college', 'library', 'museum', 'park', 'theater',
    'cinema', 'gas station', 'parking', 'bank', 'atm', 'grocery store',
    'supermarket', 'bakery', 'butcher', 'hardware store', 'bookstore'
  ];
  
  // Check for business types in query
  let businessType = null;
  for (const type of businessTypes) {
    if (query.toLowerCase().includes(type)) {
      businessType = type;
      break;
    }
  }
  
  // If no specific business type found, search for generic terms
  if (!businessType) {
    const genericBusinessTerms = ['place', 'business', 'establishment', 'service'];
    for (const term of genericBusinessTerms) {
      if (query.toLowerCase().includes(term)) {
        // Use words before or after the generic term
        const words = query.split(/\s+/);
        const index = words.findIndex(w => w.toLowerCase() === term);
        
        if (index > 0) {
          // Use word before the generic term
          businessType = words[index - 1] + ' ' + term;
        } else if (index < words.length - 1) {
          // Use word after the generic term
          businessType = term + ' ' + words[index + 1];
        } else {
          businessType = term;
        }
        break;
      }
    }
  }
  
  // Default to full query if no business type detected
  if (!businessType) {
    businessType = query;
  }
  
  // Extract qualifiers
  const qualifiers = extractQualifiers(query, businessType);
  
  return {
    businessType,
    qualifiers
  };
}

/**
 * Extract qualifiers from query
 */
function extractQualifiers(query, businessType) {
  // Common qualifier categories
  const qualifierCategories = {
    price: ['cheap', 'budget', 'expensive', 'luxury', 'affordable', 'high-end'],
    rating: ['best', 'top', 'highly rated', '5-star', 'popular'],
    food: ['italian', 'chinese', 'mexican', 'thai', 'indian', 'japanese', 'french'],
    amenities: ['outdoor seating', 'wifi', 'delivery', 'takeout', 'drive-thru', 'open late', '24 hour'],
    atmosphere: ['quiet', 'romantic', 'family-friendly', 'casual', 'formal']
  };
  
  // Flatten qualifier list
  const allQualifiers = Object.values(qualifierCategories).flat();
  
  // Find qualifiers in query
  const foundQualifiers = [];
  for (const qualifier of allQualifiers) {
    if (query.toLowerCase().includes(qualifier)) {
      foundQualifiers.push(qualifier);
    }
  }
  
  return foundQualifiers;
}

/**
 * Check if query already contains location information
 */
function checkLocationInQuery(query) {
  // Check for location indicators
  const locationPatterns = [
    /\bin\s+[A-Z][a-z]+/i,       // "in City"
    /\bnear\s+[A-Z][a-z]+/i,     // "near Place"
    /\baround\s+[A-Z][a-z]+/i,   // "around Area"
    /\bin\s+the\s+[A-Z][a-z]+/i, // "in the District"
    /near\s+me/i,                // "near me"
    /close\s+by/i,               // "close by"
    /nearby/i,                   // "nearby"
    /\b[A-Z][a-z]+,\s*[A-Z]{2}\b/i // "City, ST"
  ];
  
  for (const pattern of locationPatterns) {
    if (pattern.test(query)) {
      return true;
    }
  }
  
  return false;
}

/**
 * Process local search results with enhanced metadata
 * 
 * @param {Array} results - Raw local search results
 * @param {string} query - Original search query
 * @returns {Array} Enhanced local search results
 */
function processLocalSearchResults(results, query) {
  if (!results || results.length === 0) {
    return [];
  }
  
  // Extract user preferences from query
  const preferences = extractUserPreferences(query);
  
  return results.map(result => {
    // Calculate distance display
    const distanceDisplay = formatDistance(result.distance);
    
    // Format hours
    const hoursDisplay = formatHours(result.hours);
    
    // Calculate relevance score based on preferences
    const relevanceScore = calculateLocalRelevance(result, preferences);
    
    // Calculate satisfaction likelihood
    const satisfactionLikelihood = calculateSatisfactionLikelihood(result, preferences);
    
    return {
      ...result,
      displayData: {
        distanceDisplay,
        hoursDisplay,
        statusDisplay: getStatusDisplay(result.hours),
        priceDisplay: '$'.repeat(result.price_level || 1),
        topReviewSnippet: selectTopReviewSnippet(result.reviews, preferences)
      },
      matchData: {
        relevanceScore,
        satisfactionLikelihood,
        matchedPreferences: getMatchedPreferences(result, preferences),
        preferenceMissing: getMissingPreferences(result, preferences)
      }
    };
  })
  .sort((a, b) => b.matchData.relevanceScore - a.matchData.relevanceScore);
}

/**
 * Extract user preferences from query
 */
function extractUserPreferences(query) {
  const preferences = {
    price: null,
    rating: null,
    distance: null,
    cuisine: null,
    amenities: [],
    atmosphere: null
  };
  
  // Extract price preference
  if (/cheap|budget|inexpensive|affordable/i.test(query)) {
    preferences.price = 'low';
  } else if (/expensive|luxury|high-end|upscale/i.test(query)) {
    preferences.price = 'high';
  } else if (/moderate|mid-range|reasonable/i.test(query)) {
    preferences.price = 'medium';
  }
  
  // Extract rating preference
  if (/best|top|highest rated|excellent/i.test(query)) {
    preferences.rating = 'high';
  } else if (/good|well-rated|quality/i.test(query)) {
    preferences.rating = 'medium';
  }
  
  // Extract distance preference
  if (/nearby|close|walking distance|close by/i.test(query)) {
    preferences.distance = 'close';
  } else if (/within \d+ miles/i.test(query)) {
    const match = query.match(/within (\d+) miles/i);
    if (match) {
      preferences.distance = parseInt(match[1]);
    }
  }
  
  // Extract cuisine preference (simplified)
  const cuisines = ['italian', 'chinese', 'mexican', 'japanese', 'indian', 'thai', 
                    'french', 'greek', 'spanish', 'mediterranean', 'american', 
                    'bbq', 'vegan', 'vegetarian', 'gluten-free'];
  
  for (const cuisine of cuisines) {
    if (query.toLowerCase().includes(cuisine)) {
      preferences.cuisine = cuisine;
      break;
    }
  }
  
  // Extract amenities preferences
  const amenities = ['outdoor seating', 'patio', 'wifi', 'parking', 'takeout', 
                     'delivery', 'reservations', 'wheelchair accessible', 
                     'live music', 'happy hour', 'kid-friendly'];
  
  for (const amenity of amenities) {
    if (query.toLowerCase().includes(amenity)) {
      preferences.amenities.push(amenity);
    }
  }
  
  // Extract atmosphere preference
  const atmospheres = ['quiet', 'romantic', 'cozy', 'casual', 'fancy', 'formal', 
                       'family-friendly', 'vibrant', 'trendy', 'traditional'];
  
  for (const atmosphere of atmospheres) {
    if (query.toLowerCase().includes(atmosphere)) {
      preferences.atmosphere = atmosphere;
      break;
    }
  }
  
  return preferences;
}

/**
 * Calculate local result relevance based on user preferences
 */
function calculateLocalRelevance(result, preferences) {
  let score = 0.5; // Base score
  
  // Price match
  if (preferences.price && result.price_level) {
    if (preferences.price === 'low' && result.price_level <= 2) {
      score += 0.1;
    } else if (preferences.price === 'medium' && result.price_level === 2 || result.price_level === 3) {
      score += 0.1;
    } else if (preferences.price === 'high' && result.price_level >= 3) {
      score += 0.1;
    }
  }
  
  // Rating match
  if (preferences.rating && result.rating) {
    if (preferences.rating === 'high' && result.rating >= 4.5) {
      score += 0.15;
    } else if (preferences.rating === 'medium' && result.rating >= 4.0) {
      score += 0.1;
    } else if (preferences.rating === 'high' && result.rating >= 4.0) {
      score += 0.05; // Partial match
    }
  }
  
  // Distance match
  if (preferences.distance && result.distance) {
    if (preferences.distance === 'close' && result.distance <= 1) {
      score += 0.15;
    } else if (typeof preferences.distance === 'number' && result.distance <= preferences.distance) {
      score += 0.15;
    }
  }
  
  // Cuisine match
  if (preferences.cuisine && result.categories) {
    if (result.categories.some(cat => cat.toLowerCase().includes(preferences.cuisine))) {
      score += 0.2;
    }
  }
  
  // Amenities match
  if (preferences.amenities.length > 0 && result.amenities) {
    const matchedAmenities = preferences.amenities.filter(amenity => 
      result.amenities.some(a => a.toLowerCase().includes(amenity))
    );
    
    if (matchedAmenities.length > 0) {
      score += 0.1 * Math.min(1, matchedAmenities.length / preferences.amenities.length);
    }
  }
  
  // Atmosphere match
  if (preferences.atmosphere && result.atmosphere) {
    if (result.atmosphere.toLowerCase().includes(preferences.atmosphere)) {
      score += 0.1;
    }
  }
  
  return Math.min(1, score);
}

/**
 * Calculate likelihood of user satisfaction with this result
 */
function calculateSatisfactionLikelihood(result, preferences) {
  // This would be more sophisticated in production
  // Simplified version based on rating, relevance and reviews
  
  // Start with the normalized rating
  let satisfaction = result.rating ? (result.rating / 5) * 0.6 : 0.3;
  
  // Consider number of reviews (more reviews = more confidence)
  const reviewFactor = result.review_count ? 
    Math.min(0.2, (result.review_count / 100) * 0.2) : 0;
  
  satisfaction += reviewFactor;
  
  // Consider matched preferences
  const matchedPreferences = getMatchedPreferences(result, preferences);
  const matchRate = Object.keys(preferences).length > 0 ? 
    matchedPreferences.length / Object.keys(preferences).length : 0;
  
  satisfaction += matchRate * 0.2;
  
  return Math.min(1, satisfaction);
}

/**
 * Get list of matched preferences
 */
function getMatchedPreferences(result, preferences) {
  const matched = [];
  
  if (preferences.price && result.price_level) {
    if ((preferences.price === 'low' && result.price_level <= 2) ||
        (preferences.price === 'medium' && (result.price_level === 2 || result.price_level === 3)) ||
        (preferences.price === 'high' && result.price_level >= 3)) {
      matched.push('price');
    }
  }
  
  if (preferences.rating && result.rating) {
    if ((preferences.rating === 'high' && result.rating >= 4.5) ||
        (preferences.rating === 'medium' && result.rating >= 4.0)) {
      matched.push('rating');
    }
  }
  
  if (preferences.distance && result.distance) {
    if ((preferences.distance === 'close' && result.distance <= 1) ||
        (typeof preferences.distance === 'number' && result.distance <= preferences.distance)) {
      matched.push('distance');
    }
  }
  
  if (preferences.cuisine && result.categories) {
    if (result.categories.some(cat => cat.toLowerCase().includes(preferences.cuisine))) {
      matched.push('cuisine');
    }
  }
  
  if (preferences.atmosphere && result.atmosphere) {
    if (result.atmosphere.toLowerCase().includes(preferences.atmosphere)) {
      matched.push('atmosphere');
    }
  }
  
  return matched;
}

/**
 * Get list of missing preferences
 */
function getMissingPreferences(result, preferences) {
  const matched = getMatchedPreferences(result, preferences);
  const allPreferences = Object.keys(preferences).filter(p => 
    p !== 'amenities' && preferences[p] !== null
  );
  
  if (preferences.amenities && preferences.amenities.length > 0) {
    allPreferences.push('amenities');
  }
  
  return allPreferences.filter(p => !matched.includes(p));
}

/**
 * Format distance for display
 */
function formatDistance(distance) {
  if (distance === undefined || distance === null) {
    return 'Distance unknown';
  }
  
  if (distance < 0.1) {
    return 'Very close';
  } else if (distance < 1) {
    return `${(distance * 1000).toFixed(0)} meters away`;
  } else {
    return `${distance.toFixed(1)} miles away`;
  }
}

/**
 * Format hours for display
 */
function formatHours(hours) {
  if (!hours) {
    return 'Hours not available';
  }
  
  if (hours.current_status === 'open') {
    if (hours.closing_time) {
      return `Open until ${hours.closing_time}`;
    } else {
      return 'Currently open';
    }
  } else if (hours.current_status === 'closed') {
    if (hours.opening_time) {
      return `Closed. Opens at ${hours.opening_time}`;
    } else {
      return 'Currently closed';
    }
  }
  
  return 'Hours not available';
}

/**
 * Get status display text
 */
function getStatusDisplay(hours) {
  if (!hours) {
    return { text: 'Status unknown', class: 'unknown' };
  }
  
  if (hours.current_status === 'open') {
    return { text: 'Open Now', class: 'open' };
  } else {
    return { text: 'Closed', class: 'closed' };
  }
}

/**
 * Select the most relevant review snippet based on user preferences
 */
function selectTopReviewSnippet(reviews, preferences) {
  if (!reviews || reviews.length === 0) {
    return '';
  }
  
  // If no specific preferences, just return the highest rated review
  if (Object.values(preferences).every(v => v === null || (Array.isArray(v) && v.length === 0))) {
    return reviews.sort((a, b) => b.rating - a.rating)[0].text;
  }
  
  // Look for reviews that mention user preferences
  const relevantReviews = [];
  
  for (const review of reviews) {
    let relevanceScore = 0;
    
    // Check for price mentions
    if (preferences.price && review.text.match(/price|cost|expensive|cheap|affordable/i)) {
      relevanceScore += 1;
    }
    
    // Check for cuisine mentions
    if (preferences.cuisine && review.text.toLowerCase().includes(preferences.cuisine)) {
      relevanceScore += 2;
    }
    
    // Check for amenities mentions
    if (preferences.amenities && preferences.amenities.length > 0) {
      for (const amenity of preferences.amenities) {
        if (review.text.toLowerCase().includes(amenity)) {
          relevanceScore += 2;
        }
      }
    }
    
    // Check for atmosphere mentions
    if (preferences.atmosphere && review.text.toLowerCase().includes(preferences.atmosphere)) {
      relevanceScore += 2;
    }
    
    // Add to relevant reviews if it has any relevance
    if (relevanceScore > 0) {
      relevantReviews.push({
        ...review,
        relevanceScore
      });
    }
  }
  
  // If we found relevant reviews, return the most relevant one
  if (relevantReviews.length > 0) {
    return relevantReviews.sort((a, b) => b.relevanceScore - a.relevanceScore)[0].text;
  }
  
  // Otherwise, just return the highest rated review
  return reviews.sort((a, b) => b.rating - a.rating)[0].text;
}
```

## Best Practices Checklist

Before executing any search operation, verify:

- [ ] Query has sufficient specificity for the information need
- [ ] Temporal considerations have been addressed (if applicable)
- [ ] Source quality expectations are reflected in the query
- [ ] Multiple query formulations have been considered for complex topics
- [ ] Appropriate search capability has been selected (web vs. local)
- [ ] Result processing approach matches the information need
- [ ] Integration with other capabilities is structured appropriately

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2025-02-26 | Initial framework specification |
