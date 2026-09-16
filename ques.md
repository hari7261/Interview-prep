
---

# 1. LLM FUNDAMENTALS — WHY / HOW / WHEN

### Core architecture

1. Why are Transformers better suited to modern LLMs than RNNs?
2. How does self-attention actually help an LLM understand context?
3. Why do we need positional information in Transformers?
4. Why is causal attention required for autoregressive generation?
5. When would you choose an encoder-only model vs decoder-only model?
6. Why are decoder-only models dominant for generative applications?
7. What happens when the context window becomes very large?
8. Why doesn't a larger context window automatically mean better answers?
9. How does context length affect latency and cost?
10. When would you intentionally limit context even if the model supports a huge context window?
11. Why can an LLM give different answers to the same question?
12. How does temperature affect production behavior?
13. When would you use temperature 0?
14. Why can temperature 0 still produce unexpected results?
15. When would top-p be preferable to temperature tuning?
16. Why can increasing model size improve reasoning?
17. When is a smaller model actually better than a larger model?
18. How would you decide between two models with similar benchmark scores?
19. Why should benchmark scores not be your only model-selection criterion?
20. How would you benchmark models for your specific production workload?

### Tokens

21. Why do tokens matter beyond context length?
22. How do tokens affect cost?
23. How do tokens affect latency?
24. Why can two prompts with the same character length have different token counts?
25. How would you reduce token usage without reducing answer quality?
26. When does prompt compression become dangerous?
27. Why can sending the entire conversation history every time be a bad architecture?

---

# 2. MODEL SELECTION & ROUTING

28. When would you use a large reasoning model?
29. When would you use a smaller model?
30. Why not use the most powerful model for everything?
31. How would you route requests between three different models?
32. What signals would your router use?
33. Would you route based on user intent, complexity, token count, or something else?
34. How would you evaluate whether model routing actually saves money?
35. What happens if the router itself makes the wrong decision?
36. When would you use a model cascade?
37. How would you implement model fallback?
38. Why is fallback different from retry?
39. When should you **not** fallback to another model?
40. If Model A produces a bad answer, how do you know whether Model B will help?
41. How would you handle provider outage without silently changing behavior?
42. How would you maintain consistent structured output across different models?

---

# 3. PROMPT ENGINEERING

43. Why should system instructions be separated from user content?
44. Why shouldn't prompts contain business authorization logic?
45. What should go into the system prompt versus backend code?
46. When is few-shot prompting useful?
47. When does few-shot prompting become expensive?
48. How would you design a prompt for structured JSON output?
49. What happens when the model ignores your output format?
50. How would you recover from malformed JSON?
51. Why isn't “Please don't hallucinate” a useful hallucination-control strategy?
52. How would you design a prompt that forces evidence-based answers?
53. When would you use chain-of-thought-style reasoning internally versus structured intermediate outputs?
54. Why shouldn't you blindly expose internal reasoning to users?
55. How would you version prompts in production?
56. How would you know whether a prompt change improved the system?
57. How would you roll back a bad prompt deployment?
58. What would you log about prompts?
59. What prompt information should you **not** log?

---

# 4. RAG — CORE ARCHITECTURE

60. Why do we need RAG if LLMs already contain knowledge?
61. When is RAG better than fine-tuning?
62. When is RAG unnecessary?
63. Why can RAG reduce hallucination?
64. Why doesn't RAG automatically eliminate hallucination?
65. Design an enterprise RAG pipeline from document ingestion to answer generation.
66. Where would you store raw documents?
67. Where would you store chunks?
68. Where would you store embeddings?
69. What metadata would you attach to each chunk?
70. Why is metadata important?
71. How would you implement document versioning?
72. How would you handle document deletion?
73. What happens when a document changes?
74. How would you prevent stale documents from being retrieved?
75. How would you handle duplicate documents?
76. How would you handle 10 million documents?
77. When would you re-embed the entire corpus?
78. When would you perform incremental embedding?

---

# 5. CHUNKING

79. Why does chunk size matter?
80. When would you use fixed-size chunking?
81. When would you use semantic chunking?
82. When would you use structure-aware chunking?
83. Why can chunks that are too small hurt retrieval?
84. Why can chunks that are too large hurt retrieval?
85. How would you determine the correct chunk size?
86. Would you use the same chunk size for legal documents and source code?
87. How would you chunk tables?
88. How would you chunk long technical documents?
89. How would you preserve relationships between chunks?
90. When would parent-child retrieval help?
91. How would you evaluate different chunking strategies?

---

# 6. EMBEDDINGS & RETRIEVAL

92. What exactly does an embedding represent?
93. Why use embeddings instead of keyword search?
94. When is keyword search better than vector search?
95. Why would you use hybrid search?
96. How does BM25 work conceptually?
97. When would you choose BM25 over embeddings?
98. How would you combine lexical and semantic scores?
99. Why can vector similarity return semantically related but incorrect documents?
100. How would you improve retrieval precision?
101. How would you improve retrieval recall?
102. What is the difference between retrieval recall and answer correctness?
103. Why isn't top-K retrieval always enough?
104. How would you choose K?
105. What happens if K is too high?
106. What happens if K is too low?
107. When would you use metadata filtering before vector search?
108. When would you use reranking?
109. Why does reranking improve RAG?
110. When is reranking not worth the latency?
111. How would you design a hybrid retrieval system?

---

# 7. ADVANCED RAG

112. What is query rewriting?
113. When should an agent rewrite a user's query?
114. Why can query rewriting make retrieval worse?
115. When would you use multi-query retrieval?
116. When would you use HyDE-style retrieval?
117. What is contextual compression?
118. When would you use it?
119. What is parent-child retrieval?
120. When is Graph RAG useful?
121. When is Graph RAG unnecessary complexity?
122. When would you use multi-hop retrieval?
123. How would you detect that the first retrieval wasn't sufficient?
124. How would you build an agentic RAG system?
125. When should an agent stop searching?
126. How do you prevent an agent from searching forever?
127. How do you determine whether another retrieval call is worth the cost?

---

# 8. RAG DEBUGGING

128. Your RAG system suddenly becomes 20% less accurate. **How do you investigate?**
129. How do you determine whether the problem is ingestion or retrieval?
130. How do you determine whether retrieval is correct but generation is wrong?
131. What metrics would you check first?
132. How would you compare the old and new retrieval pipeline?
133. What if retrieval recall improved but user satisfaction decreased?
134. What if your top-5 documents look relevant but the answer is still wrong?
135. What if the correct document exists but isn't retrieved?
136. What if the correct document is retrieved but the LLM ignores it?
137. What if the answer is technically correct but unsupported by retrieved evidence?
138. How would you detect stale knowledge?
139. How would you test RAG without relying only on human reviewers?
140. How would you build a golden RAG evaluation dataset?

---

# 9. AGENTS

141. What exactly makes a system an agent?
142. Why isn't every tool-calling LLM an agent?
143. When should you use an agent?
144. When should you **not** use an agent?
145. Why not build everything as an agent?
146. What problems do agents solve that workflows don't?
147. What problems do workflows solve better than agents?
148. How does an agent decide which tool to call?
149. Where does the agent's state live?
150. What is the difference between agent state and conversation history?
151. What causes agent loops?
152. How do you detect an agent loop?
153. How do you stop an agent loop?
154. What should happen when the agent doesn't know what to do next?
155. How do you determine whether an agent has completed its task?
156. What does “done” actually mean for an agent?

---

# 10. AGENT RUNTIME

This is **very important for you**.

157. Why do we need a runtime instead of simply writing an LLM → tool loop?
158. What responsibilities should the runtime own?
159. What responsibilities should the LLM own?
160. What responsibilities should deterministic backend code own?
161. How would you design an agent runtime from scratch?
162. What state would you persist?
163. What should happen if the worker crashes after a tool succeeds?
164. How would you resume an interrupted agent?
165. How would you checkpoint an agent?
166. When should you checkpoint?
167. How frequently should you checkpoint?
168. What happens if checkpoint persistence fails?
169. How would you replay an agent execution?
170. Why is replay useful?
171. What would you store for replay?
172. How would you make agent execution auditable?
173. How would you cancel a running agent?
174. How would you pause an agent?
175. How would you resume it after six hours?
176. How would you enforce execution budgets?
177. What happens when an agent exceeds its token budget?
178. What happens when it exceeds its tool-call budget?
179. What happens when it exceeds its time budget?

---

# 11. STATE MACHINES

180. Why should agent state be explicit?
181. Why shouldn't conversation history be your source of truth?
182. What states would you define for an enterprise support agent?
183. What happens if an invalid state transition occurs?
184. How would you guarantee valid transitions?
185. Where would state be persisted?
186. How would you handle concurrent updates to the same agent run?
187. How would you recover from a partially completed state transition?
188. How would you make state transitions idempotent?
189. What is the difference between workflow state and business state?

---

# 12. TOOL CALLING

190. How does tool calling work internally?
191. Why should tools have strict schemas?
192. Why shouldn't the LLM directly access your database?
193. How would you expose database capabilities safely?
194. How would you validate tool arguments?
195. What if the model sends an invalid customer ID?
196. What if the model sends the wrong refund amount?
197. What if the model calls the same tool five times?
198. How would you prevent duplicate side effects?
199. How would you design an idempotent tool?
200. Which tools should be read-only?
201. Which tools should require approval?
202. How would you classify tool risk?
203. How would you dynamically restrict tools based on user permissions?
204. Can an agent call tools the user doesn't have access to?
205. What happens if a tool returns malicious instructions?

---

# 13. TOOL SECURITY

206. Why isn't tool description enough for security?
207. Why shouldn't the LLM be trusted with authorization?
208. Where should authorization happen?
209. Where should business rules happen?
210. Where should parameter validation happen?
211. How would you prevent an agent from deleting production data?
212. How would you prevent an agent from accessing another tenant's data?
213. How would you implement least privilege for agents?
214. Would every agent have the same tool permissions?
215. How would you audit tool execution?
216. What information would you record?
217. How would you investigate an unsafe tool call after it happened?

---

# 14. AGENT MEMORY

218. Why do agents need memory?
219. When does memory actually make the system worse?
220. What belongs in short-term memory?
221. What belongs in long-term memory?
222. What should **never** automatically become long-term memory?
223. How would you decide what to remember?
224. How would you retrieve relevant memories?
225. How would you prevent memory explosion?
226. How would you handle conflicting memories?
227. What if the user says something today that contradicts a memory from six months ago?
228. How would you expire memories?
229. How would you let users delete memories?
230. How would you prevent memory from overriding company policy?
231. Where would you store memory?
232. SQL or vector DB for memory — when and why?
233. How would you evaluate memory quality?

---

# 15. MULTI-AGENT

234. Why use multiple agents?
235. When is multi-agent architecture justified?
236. Why not simply use one powerful agent?
237. What are the disadvantages of multi-agent systems?
238. How would agents communicate?
239. Would agents share memory?
240. Would agents share tools?
241. How would you enforce permissions between agents?
242. Who controls the other agents?
243. What happens when two agents disagree?
244. How would you debug a multi-agent failure?
245. How would you trace a task across five agents?
246. How would you prevent agents from repeatedly delegating to each other?
247. When would you use supervisor architecture?
248. When would you use peer-to-peer agents?
249. When would you use parallel agents?
250. How would you determine whether five agents are actually better than one?

---

# 16. AGENT VS WORKFLOW

251. You have 10 deterministic business steps. Would you use an agent?
252. You have 5 possible tools and unknown task paths. Would you use an agent?
253. Why not let the LLM control every step?
254. Where should deterministic logic remain?
255. How would you combine workflow + agent?
256. Can an agent exist inside a deterministic workflow?
257. Can a workflow contain an LLM?
258. Give an example where using an agent would be a mistake.
259. Give an example where a deterministic workflow would be a mistake.
260. What is the production sweet spot between workflow and fully autonomous agent?

---

# 17. HUMAN-IN-THE-LOOP

261. Which agent actions should require human approval?
262. Why shouldn't every action require approval?
263. How would you classify action risk?
264. How would you implement approval asynchronously?
265. What happens if the user never approves?
266. What happens if approval expires?
267. What happens if the underlying data changes after approval?
268. Should an approval remain valid if the agent changes the action parameters?
269. How do you guarantee the approved action is exactly the action executed?
270. How would you audit approval?
271. How would you resume the agent after approval?
272. When should you escalate to a human instead of retrying?

---

# 18. PROMPT INJECTION / AI SECURITY

273. What is prompt injection?
274. What is indirect prompt injection?
275. How can an email attack an agent?
276. How can a retrieved document attack an agent?
277. How can a web page attack an agent?
278. Why doesn't a stronger system prompt completely solve prompt injection?
279. How would you design an agent that processes untrusted emails?
280. How would you isolate untrusted content?
281. How would you prevent retrieved content from becoming instructions?
282. How would you prevent tool-output injection?
283. How would you prevent data exfiltration?
284. What if the user asks the agent to reveal its system prompt?
285. What if a document tells the agent to call a dangerous tool?
286. How would you detect suspicious agent behavior?
287. How would you build defense-in-depth for agents?

---

# 19. GUARDRAILS

288. What should be handled by an LLM guardrail?
289. What should be handled by deterministic code?
290. Why can't guardrails guarantee safety?
291. How would you validate an LLM's decision?
292. How would you validate structured output?
293. How would you validate tool parameters?
294. How would you enforce financial limits?
295. How would you enforce tenant boundaries?
296. How would you implement output moderation?
297. What happens if guardrail evaluation itself fails?
298. Should guardrails run before or after tool execution?
299. Which guardrails must happen **before side effects**?

---

# 20. EVALUATION

This is a **must-strengthen area for you**.

300. Why is evaluating an LLM application harder than evaluating normal software?
301. What exactly does “good answer” mean?
302. How would you build an evaluation dataset?
303. What makes a good golden dataset?
304. How would you evaluate a RAG system?
305. How would you evaluate an agent?
306. How would you evaluate tool selection?
307. How would you evaluate tool arguments?
308. How would you evaluate hallucination?
309. How would you evaluate groundedness?
310. How would you evaluate task completion?
311. What is LLM-as-a-judge?
312. When is LLM-as-a-judge unreliable?
313. How would you validate your evaluator?
314. How would you detect regression after changing a prompt?
315. How would you compare two models?
316. How would you measure production quality?
317. What metrics would you put on an AI dashboard?
318. What is offline evaluation?
319. What is online evaluation?
320. How would you combine automated evaluation with human evaluation?

---

# 21. AGENT EVALUATION

321. Agent completes the task in 3 steps vs 12 steps. Which is better?
322. Agent gives the correct answer but uses the wrong tool. Is that a success?
323. Agent reaches the correct result but violates policy temporarily. Is that success?
324. How would you score an agent trajectory?
325. How would you detect unnecessary tool calls?
326. How would you measure agent efficiency?
327. How would you evaluate recovery after tool failure?
328. How would you test rare failure paths?
329. How would you create adversarial agent tests?
330. How would you test prompt-injection resistance?
331. How would you test long-running agent reliability?

---

# 22. HALLUCINATION & GROUNDING

332. Why do LLMs hallucinate?
333. Why doesn't RAG eliminate hallucination?
334. How would you reduce hallucination?
335. How would you detect hallucination automatically?
336. What if retrieved evidence contradicts the model's prior knowledge?
337. Which source should win?
338. What if retrieved documents contradict each other?
339. How should the agent handle missing information?
340. Should the model ever answer without retrieval evidence?
341. How would you force citation-backed responses?
342. How would you verify citations?
343. What does “grounded answer” actually mean?

---

# 23. OBSERVABILITY

344. What should you log for every agent execution?
345. What is a correlation ID?
346. What is a trace ID?
347. What is a span?
348. How would you trace a 15-step agent execution?
349. How would you debug a 60-second agent request?
350. How would you determine where latency is coming from?
351. What AI-specific metrics would you monitor?
352. How would you monitor tool failures?
353. How would you monitor agent loops?
354. How would you monitor hallucination?
355. How would you monitor cost?
356. How would you monitor model quality after deployment?
357. What information should never be logged?

---

# 24. LATENCY

358. Your agent takes 45 seconds. How do you diagnose it?
359. What if the LLM takes only 2 seconds but the total request takes 45 seconds?
360. What if retrieval takes 15 seconds?
361. What if the agent performs five sequential tool calls?
362. Which calls can be parallelized?
363. When should you avoid parallelization?
364. How does streaming improve perceived latency?
365. Does streaming actually reduce backend latency?
366. How would you reduce agent latency by 50%?
367. How would you measure the impact of each optimization?

---

# 25. COST

368. Your AI system costs ₹10 per task. How do you reduce it to ₹5?
369. How would you identify where the cost is coming from?
370. Would you switch to a smaller model?
371. What could go wrong if you do?
372. How can caching reduce cost?
373. When does caching become dangerous?
374. How would you reduce context size?
375. How would you reduce unnecessary tool calls?
376. How would you enforce cost budgets?
377. Would you give every tenant unlimited agent execution?
378. How would you calculate cost per successful task?

---

# 26. RELIABILITY

379. What happens when the LLM provider is unavailable?
380. What happens when the vector DB is unavailable?
381. What happens when a tool times out?
382. What happens when a tool partially succeeds?
383. What happens when the worker crashes?
384. What happens when a queue message is duplicated?
385. What happens when the same refund executes twice?
386. What happens if the agent loses state?
387. How would you make the system resumable?
388. How would you classify retryable vs non-retryable failures?
389. Why is blindly retrying dangerous?
390. When would you use exponential backoff?
391. When would you use a circuit breaker?
392. When would you use a dead-letter queue?
393. When would you escalate to a human?

---

# 27. DISTRIBUTED SYSTEMS FOR AGENTS

394. Why are agent systems fundamentally distributed systems?
395. What happens with at-least-once message delivery?
396. How do you achieve idempotency?
397. Where should idempotency keys live?
398. How would you handle race conditions between two agent workers?
399. How would you lock an agent run?
400. What happens if two workers process the same task?
401. How would you prevent duplicate side effects?
402. How would you handle eventual consistency?
403. How would you reconcile inconsistent state?
404. How would you design an agent system for millions of tasks per day?

---

# 28. EVENT-DRIVEN AGENTS

405. Why would you use queues for agents?
406. When should an agent execution be asynchronous?
407. When should it be synchronous?
408. How would you design email → queue → agent processing?
409. Why shouldn't a 2-minute agent execution block an HTTP request?
410. How would you provide status to the frontend?
411. How would you stream progress?
412. How would you handle backpressure?
413. What happens if the queue grows faster than workers can process?
414. How would you autoscale workers?
415. How would you replay failed events?

---

# 29. FRAMEWORKS

416. Why LangGraph?
417. Why not LangGraph?
418. Why AutoGen?
419. Why not AutoGen?
420. When would you use CrewAI?
421. When would you avoid agent frameworks completely?
422. What does a framework actually give you?
423. What should remain under your control?
424. How would you evaluate an agent framework?
425. What framework limitations would make you build your own runtime?
426. Can a framework become a production bottleneck?
427. How would you migrate away from a framework later?
428. How would you prevent framework lock-in?

---

# 30. MCP

429. What problem does MCP solve?
430. Why not just use REST APIs?
431. When would MCP be useful?
432. When would MCP be unnecessary?
433. How does MCP change tool discovery?
434. What are the security implications of dynamic tool discovery?
435. Should an agent automatically trust every MCP tool?
436. How would you authorize MCP tools?
437. How would you audit MCP tool usage?
438. Where does MCP fit into your agent runtime?

---

# 31. FINE-TUNING

439. When would you fine-tune instead of using RAG?
440. When would fine-tuning be a bad idea?
441. How would you determine whether fine-tuning is necessary?
442. What kind of dataset would you need?
443. How would you evaluate a fine-tuned model?
444. What can fine-tuning improve?
445. What can fine-tuning **not** solve?
446. Why can't fine-tuning replace real-time company data?
447. When would you use LoRA?
448. When would you use full fine-tuning?
449. How would you detect regression after fine-tuning?

---

# 32. MULTIMODAL AI

450. When would you use a vision-language model?
451. When would you use OCR + LLM instead?
452. Why can multimodal models hallucinate visual information?
453. How would you process 1 million invoices?
454. How would you extract structured data from documents?
455. When would you use specialized document AI instead of a general VLM?
456. How would you evaluate multimodal extraction?
457. How would you control multimodal inference cost?

---

# 33. AI PLATFORM DESIGN

458. Design a centralized model gateway for your company.
459. Why do you need a model gateway?
460. What happens if every team directly calls OpenAI/Anthropic/etc.?
461. How would you implement model routing?
462. How would you implement tenant-level budgets?
463. How would you implement centralized observability?
464. How would you manage prompt versions?
465. How would you manage model versions?
466. How would you support multiple providers?
467. How would you handle provider-specific API differences?
468. How would you prevent one team's workload from affecting another?
469. How would you design an enterprise agent platform?
470. Which parts should be centralized?
471. Which parts should remain team-owned?

---

# 34. MULTI-TENANT AI

472. How do you isolate customer data?
473. How do you isolate vector search?
474. How do you isolate memory?
475. How do you isolate agent tools?
476. How do you prevent cross-tenant retrieval?
477. Where should tenant authorization happen?
478. Can metadata filtering alone guarantee isolation?
479. How would you handle tenant-specific prompts?
480. How would you handle tenant-specific models?
481. How would you calculate cost per tenant?

---

# 35. AI DATABASE / DATA ARCHITECTURE

482. SQL vs vector DB — when and why?
483. Why not store everything in a vector database?
484. Why not store embeddings in PostgreSQL?
485. When is pgvector sufficient?
486. When would you need a dedicated vector DB?
487. How would you store conversation history?
488. How would you store agent state?
489. How would you store long-term memory?
490. How would you store evaluation data?
491. How would you store traces?
492. How would you design retention policies?

---

# 36. CACHING

493. What can you cache in an AI system?
494. Should you cache LLM responses?
495. When is response caching dangerous?
496. When can semantic caching help?
497. Should retrieval results be cached?
498. How do you invalidate cached knowledge?
499. How does caching affect correctness?
500. How would you measure whether caching is worth it?

---

# 37. PRODUCTION INCIDENTS

501. Agent cost suddenly increases 3×. Diagnose.
502. Agent latency suddenly increases 5×. Diagnose.
503. RAG answers suddenly become worse. Diagnose.
504. Agent starts repeatedly calling one tool. Diagnose.
505. Agent sends duplicate emails. Diagnose.
506. Agent refunds customers incorrectly. Diagnose.
507. Agent retrieves another tenant's document. Diagnose.
508. Model provider starts returning malformed JSON. Diagnose.
509. Queue backlog grows rapidly. Diagnose.
510. Workers keep restarting. Diagnose.
511. Human approvals stop resuming agents. Diagnose.
512. Vector DB latency doubles. Diagnose.
513. A new prompt causes task success to drop 10%. Diagnose.
514. Token usage suddenly doubles. Diagnose.

---

# 38. SYSTEM DESIGN — REAL INTERVIEW QUESTIONS

515. Design an enterprise email agent.

516. Design a customer support agent.

517. Design an AI sales assistant.

518. Design an AI coding agent.

519. Design a financial operations agent.

520. Design a healthcare support agent.

521. Design an enterprise knowledge assistant.

522. Design a multi-tenant RAG platform.

523. Design an agent runtime.

524. Design a model gateway.

525. Design an AI evaluation platform.

526. Design an AI observability platform.

527. Design a long-running agent system.

528. Design an agent that processes millions of emails daily.

529. Design an agent that can execute financial transactions safely.

530. Design an agent platform where different customers have different tools and policies.

---

# 39. STAFF-LEVEL QUESTIONS

These are where I want you to eventually become **very comfortable**.

531. Your company has 50 teams independently building agents. What platform would you create?

532. Why centralize agent infrastructure?

533. What should be standardized across teams?

534. What should not be standardized?

535. How would you prevent every team from building its own RAG implementation?

536. How would you establish organization-wide AI quality standards?

537. How would you establish organization-wide AI security standards?

538. How would you measure whether AI investments are actually producing business value?

539. How would you reduce AI infrastructure costs across an organization?

540. How would you decide whether to build or buy an AI platform?

541. When should the company build its own agent runtime?

542. When should the company use a framework?

543. How would you design for provider independence?

544. How would you prevent vendor lock-in?

545. How would you introduce AI into an existing enterprise architecture without creating chaos?

---

# 40. PRINCIPAL-LEVEL QUESTIONS

546. If you were responsible for the company's entire GenAI strategy, where would you start?

547. Which AI capabilities should become platform services?

548. Which AI capabilities should remain product-specific?

549. How would you define an enterprise agent architecture standard?

550. How would you decide where autonomy is acceptable?

551. Where should humans remain in the loop?

552. How would you define risk tiers for AI actions?

553. How would you create an AI governance model?

554. How would you choose between proprietary and open-source models strategically?

555. How would you handle rapidly changing model providers?

556. How would you build an architecture that survives model changes?

557. What would you optimize first: cost, latency, quality, or autonomy?

558. How would you determine the right balance?

559. What does “production-ready agent” actually mean?

560. What would prevent you from deploying a fully autonomous agent?

---

# 41. THE HARD “WHY NOT?” QUESTIONS

These are **gold for interview preparation**.

561. Why not use a larger model?

562. Why not use RAG?

563. Why not fine-tune?

564. Why not use an agent?

565. Why not use multiple agents?

566. Why not use LangGraph?

567. Why not build your own runtime?

568. Why not use a vector database?

569. Why not use PostgreSQL + pgvector?

570. Why not use BM25?

571. Why not use semantic search?

572. Why not use hybrid search?

573. Why not cache the result?

574. Why not retry?

575. Why not fallback to another model?

576. Why not let the agent retry indefinitely?

577. Why not give the agent all tools?

578. Why not let the LLM decide authorization?

579. Why not let the agent execute refunds automatically?

580. Why not require human approval for everything?

581. Why not store all conversation history?

582. Why not store every user statement as memory?

583. Why not send the entire knowledge base to the LLM?

584. Why not use a huge context window?

585. Why not use one giant prompt?

586. Why not use five specialized agents?

587. Why not make everything asynchronous?

588. Why not make everything synchronous?

589. Why not use an open-source model?

590. Why not use the best benchmark-performing model?

---

# 42. THE HARD “WHAT IF?” QUESTIONS

591. What if the LLM is correct but the tool fails?

592. What if the tool succeeds but the LLM thinks it failed?

593. What if the tool succeeds twice?

594. What if the worker crashes after the tool succeeds?

595. What if the database updates but the event isn't published?

596. What if the event is published twice?

597. What if two agents modify the same customer record?

598. What if retrieved documents contradict each other?

599. What if the user gives contradictory instructions?

600. What if memory contradicts company policy?

601. What if the model's answer conflicts with retrieved evidence?

602. What if retrieval returns nothing?

603. What if retrieval returns too much?

604. What if the model selects the wrong tool?

605. What if the model selects the right tool but wrong parameters?

606. What if a tool returns malicious content?

607. What if an external API is unavailable for 30 minutes?

608. What if the human approval arrives after the business state changed?

609. What if the agent exceeds its cost budget halfway through?

610. What if the agent reaches maximum iterations without completing?

---

# 43. THE “DESIGN IT” QUESTIONS

611. Design a tool registry.

612. Design a policy engine for agents.

613. Design an agent state store.

614. Design an approval system.

615. Design agent checkpointing.

616. Design agent replay.

617. Design agent cancellation.

618. Design agent retry handling.

619. Design agent idempotency.

620. Design an agent execution trace.

621. Design model routing.

622. Design LLM fallback.

623. Design RAG evaluation.

624. Design agent evaluation.

625. Design prompt versioning.

626. Design model versioning.

627. Design AI cost tracking.

628. Design AI latency monitoring.

629. Design prompt-injection protection.

630. Design tenant isolation.

---

# 44. THE “EXPLAIN THE TRADEOFF” QUESTIONS

631. Accuracy vs latency — what do you optimize?

632. Accuracy vs cost — what do you optimize?

633. Agent autonomy vs safety — where is the boundary?

634. Retrieval recall vs context size — how do you balance them?

635. More tools vs simpler agent — which is better?

636. Single agent vs multiple agents?

637. Framework vs custom runtime?

638. Managed model vs self-hosted model?

639. Vector DB vs search engine?

640. Synchronous vs asynchronous execution?

641. Retry vs fallback?

642. Automation vs human approval?

643. Long-term memory vs stateless execution?

644. Large context vs retrieval?

645. Larger model vs better system architecture?

---

# 45. FINAL BOSS QUESTIONS

These are the questions I'd eventually use to test whether you're genuinely operating at **Staff/Principal level**.

646. **Design an agent platform for 100 million executions per day.**

647. **The platform must support multiple LLM providers, millions of users, hundreds of tools, human approvals, RAG, memory, and strict tenant isolation. Design it.**

648. **Your agent has 90% task success but costs 5× more than the business can afford. What do you change?**

649. **Your agent costs very little but task success is only 65%. How do you improve it?**

650. **Your agent is 95% accurate but occasionally performs catastrophic actions. How do you handle that?**

651. **Your RAG system has excellent retrieval metrics but poor user satisfaction. Explain why.**

652. **Your agent passes offline evaluations but fails in production. Why?**

653. **Your agent works perfectly with 1,000 users but collapses at 1 million. Diagnose the architecture.**

654. **Your agent framework becomes a bottleneck. What do you replace it with?**

655. **You have five agents in production and nobody can explain why they made a particular decision. How do you redesign the system?**

656. **Your company wants fully autonomous AI agents. What risks do you identify before approving the architecture?**

657. **You are given unlimited model intelligence but limited latency, cost, and reliability budgets. Design the system.**

658. **You are given a powerful LLM but it cannot be trusted with side effects. How do you build a useful autonomous system around it?**

659. **An agent must operate for three days, survive worker failures, wait for humans, call external APIs, and eventually complete a financial workflow. Design the execution architecture.**

660. **If you had to build the minimum infrastructure required to safely run enterprise agents, what would you build first and why?**

---

## How I want you to use this list

**Don't try to answer all 660.**

That would become memorization, and that's exactly what we don't want.

Instead, we'll use these as a **question bank**.

For your preparation, I'd take them in this order:

**Phase 1**

LLM → RAG → embeddings → retrieval → tool calling

**Phase 2**

Agents → workflows → runtime → state → memory → HITL

**Phase 3**

Security → prompt injection → guardrails → reliability → distributed systems

**Phase 4**

Evals → observability → latency → cost → model routing

**Phase 5**

Multi-agent → frameworks → MCP → AI platform

**Phase 6**

System design → production incidents → Staff/Principal tradeoffs

And when we practice, I won't ask:

> “What is RAG?”

I'll ask:

> **“Your RAG system retrieves the correct document 95% of the time, but the final answer is still wrong 20% of the time. How do you diagnose it?”**

That's the kind of question that forces you to **think like an engineer rather than recite definitions**.

And that's the interview preparation I think will give you the biggest jump.
