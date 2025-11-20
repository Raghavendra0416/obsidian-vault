
SESSION2-50MIN COMPLTED

www.linkedin.com/in/komal-sharma-603689157


Gen AI:
Session 2:
- How to generate a specific texts(for specific questions) by providing instructions?
- What is MML?
- what is rag?
- what are function calls?
- what is fine tuning?
- How to use a model for specific requirement?
- what is Retrieval Augmented Generation
- Difference between models?
- what can a model can do? what are it limitations?
- how does GPT, perplexity provide answers through web?
- What are agents and what do they do? and what do they use? and how functions are used in it?
- what is open source LLM?
- how to use playground?



// Find the sum upto N
// top down way
function sumTillN(N) {
  if(N === 0) {
    return 0;
  }
  return N + sumTillN(N-1);
} // O(N) time, O(1) space (ignoring the aux memory)

// Bottom up function using recursion
// for (let i = 0; i < N; i++)
function sumUptoN(i, N) {
  if(i === N) {
    return N;
  }
  return i + sumUptoN(i + 1, N);
}


console.log(sumUptoN(1, 5));