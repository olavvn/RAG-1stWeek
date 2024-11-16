# Context Recall

> Context Recall measures how many of the relevant documents were succesfully retrieved.
<br>
Calculating context recall always requires a reference to compare against

## LLM Based Context Recall
> LLMContextRecall: being computed using "user_input", "reference" and the "retrieved_contexts"
<br>
and returning the values range between 0 and 1; higher values indicating better performance.
- Using "reference" as a proxy to "reference_context".
    - easier to use than "reference_context"
    - broken down into claims that each claim in the reference answer is analyzed to determine whether it can be attributed to the retrieved context or not.
- Contect recall = 
<br>
|GT claims that can be attributed to context| / |Number of GT|

# Factual Correctness

> FactualCorrectness: A metric that can compares and evaluates the factual accuracy of the generated "response" with the "reference".
<br>
> Returning the values range between 0 and 1, with higher values indicating better performance.
1. Using the LLM for first break down the response and reference into claims
2. Using natural language inference to determine the factual overlap between the response and the reference
3. Factual overlap is quantified using precision, recall, and F1 score; can be controlled using the "mode" parameter.

## Fomulas
- True Positive(TP) = Number of claims in response that are present in reference
- False Positive(FP) = Number of claims in response that are not present in reference
- False Negative(FN) = Number of claims in reference that are not present in response
- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)
- F1 Score = 2 * Precision * Recall / (Precision + Recall)

## Controlling the Number of Claims
> Number of claims that are generated from a single sentence is determined by the level of "atomicity" and " coverage".

> Atomicity: How much a sentence is broken down into its smallest, meaningful components.
- High Atomicity: The sentence is broken down into its fundamental, indivisible claims.
- Low Atomicity: The sentence is kept more intact.

> Coverage: how comprehesively the claims represent the information in the original sentence.
- High Coverage:  The decomposed claims capture all the information present in the original sentence, preserving every detail.
- Low Coverage: The decomposed claims cover only the main points, omitting some details to provide a more generalized view.

> Practical Application
- Use High Atomicity and High Coverage when you need a detailed and comprehensive breakdown for in-depth analysis or information extraction.
- Use Low Atomicity and Low Coverage when only the key information is necessary, such as for summarization.

# Semantic similarity
> SemanticSimilarity: The assessment of the semantic resemblance between the generated answer and the ground truth.

## How It's Calculated
1. Vectorize the ground truth answer using embedding model
2. Vectorize the generated answer using the same embedding model
3. Compute the cosine similarity between two vectors.


