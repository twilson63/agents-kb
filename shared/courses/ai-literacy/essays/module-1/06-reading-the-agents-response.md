# Reading the Agent's Response

*Module 1 — Reverse Prompting | Essay 6 of 8*

---

Most people read an agent's output to decide if it's usable. That's not wrong, but it's not enough. The response also contains signals about how well the agent understood you — and those signals tell you exactly what to do next.

Once you learn to read them, you stop guessing at your next prompt.

The first thing to look for is hedging. Phrases like "you might want to consider," "depending on your situation," "this could vary" usually mean the agent didn't have enough context to commit to a direction. It's not being cautious for fun. It's telling you it made assumptions and isn't sure they're right. Your move: give it the information it was missing.

The second signal is generic language. If the output could have been written for anyone in your field, the agent didn't know enough about your specific situation. "Stakeholder alignment" and "cross-functional collaboration" are signals that the agent defaulted to industry boilerplate. It had the category right but not the specifics. Add more context about your actual situation and the language will sharpen.

The third signal is structure that doesn't match your need. An agent that produces five numbered steps when you needed a short paragraph, or a formal report when you needed a quick note — that's not bad judgment, it's a missing constraint. You didn't tell it what shape the output should take.

The fourth, and easiest to miss: when the agent asks you a clarifying question, that's not a failure. It's the agent being honest about what it needs. Answer the question directly and specifically. Agents that ask questions tend to produce better work than agents that silently guess.

None of this requires technical knowledge. It's just paying attention. Read the response the way you'd read a draft from a colleague. What did they get right? What did they assume? What question are they implicitly asking by the choices they made?

The answer to that question is your next message.

---

*Pod exercise: Run a prompt on any task in your practice pod. Read the response and annotate it: highlight one place where the agent hedged, one place where the language went generic, and one place where it made a structural choice you didn't ask for. Write one follow-up message that addresses all three. Run it and compare.*
