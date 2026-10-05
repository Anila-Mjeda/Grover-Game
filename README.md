# Grover Lab — Find the key

A self-contained classroom game about **Grover’s algorithm**, with particular attention to the oracle, the helper qubit, relative phase, and interference. Students inspect the checker’s rule, follow the joint state, predict an amplitude change, and compare measurements. The full matrices and state vectors appear underneath the activities.

## The model

* **A** is the first search qubit; **B** is the second. Together they form the search register, whose possible key labels are `00`, `01`, `10`, and `11`.
* **h** is one helper qubit, used as temporary checking workspace. There is one helper wire, even when different terms in the superposition have different helper labels.
* The **oracle is a circuit**, not another qubit: **Check → Mark phase → Clear h**.
* The **diffuser**, labelled **Boost**, acts on A and B. Its matrix is the same for every lock rule.

A component is a basis label together with its amplitude. For example, `½|101⟩` is the term with A = 1, B = 0, h = 1 and amplitude ½. The three-qubit vector has eight possible labels, ordered `000, 001, 010, 011, 100, 101, 110, 111`. The four key cards group those labels by AB. They do not represent four qubits.

This is an ideal model with four candidate keys and exactly one match. Its deliberately simple rule teaches verification rather than demonstrating a practical speedup. Other problem sizes and numbers of solutions require an appropriate number of Grover iterations.

The colour legend follows the current snapshot. When no amplitude is negative, it says **No negative amplitudes in this step**. A zero-amplitude key card says **Component absent** in place of a helper label; the physical helper qubit still exists, but that card has no populated component at this step.

## How to play

Open `index.html` in a modern browser. The page works offline, with no installation, accounts, server, or external libraries.

1. **Read the three qubit roles.** Inspect the lock rule. The default required values are A = 1 and B = 0, so the checker evaluates `f(A,B) = A × (1 − B)`. It returns 1 only when both conditions pass. Change either required value to start a round with a different matching key.
2. **Prepare the search.** Use **Next** through **H on A** and **H on B**. There are now four equal key amplitudes of +½ and four key probabilities of 25%. Superposition has not yet entangled these two search qubits.
3. **Follow Check.** Select a card or a row in the checker table. The same rule acts coherently on all terms; selecting a label only changes the teaching inspector. Within a basis label, A and B’s values are unchanged while h toggles if f = 1. The helper becomes entangled with the whole AB register.
4. **Predict the phase effect.** At **Check**, answer the phase question before advancing to **Mark phase**. Z changes the matching joint amplitude from +½ to −½ without changing any basis digit. Both amplitudes have squared magnitude ¼. **Apply Mark phase** advances to the next snapshot; you can also use Next.
5. **Undo the helper flag.** Advance to **Clear h**. Running the checker again toggles the matching helper label from 1 to 0. Other populated helper-0 labels stay 0. This is reversible uncomputing, not measurement or a physical reset. The matching amplitude stays negative. Now h factors out as the independent state `|0⟩`; A and B remain entangled with each other.
6. **Predict before Boost.** At Clear h, Next scrolls to **Predict the mirror reflection (before the “Boost” step)** and leaves the state unchanged. Choose a key with **Key to predict**, a card, or the checker table. Calculate `a′ = 2 × mean − a`, move the hollow marker with the slider, and choose **Check prediction**. Retry if needed. Repeat for other keys, then choose **Apply Boost and reveal**. The input mean here is ¼. Green output bars, worked interference sums, and measurement results remain hidden until Boost. The full maths is still available for students who want to calculate the answer themselves.
7. **Inspect interference.** After Boost, choose an output key. Each displayed contribution is a diffuser matrix weight multiplied by an input amplitude. Four positive contributions reinforce at the matching output; two positive and two negative contributions cancel at each other output. The wave picture is an analogy for adding these numbers, not travelling qubits or the state evolving in time.
8. **Explore the maths.** Each snapshot shows the exact 8 × 8 operator, its input vector, and its output vector. Matrix columns label inputs; rows label outputs. Choose an output row to inspect all eight products. Fractions are enlarged and stacked. On a narrow screen, scroll the equation horizontally. Expand the additional panels for the 4 × 4 search matrices and the calculation supporting the entanglement statements.
9. **Compare measurements.** After Boost, try **Oracle only**, **Skip the oracle**, and **Full Grover round**. Measure one or 100 fresh runs. Each run starts from `|000⟩`, applies both search H gates, runs its chosen sequence, and ends with one measurement of AB. The three experiments keep separate counts; changing them does not change the walkthrough. Theoretical probabilities and observed counts are labelled separately.

## Extra controls

* **Try the reversible check twice** follows one chosen basis label in a separate mini demo. Choose starting helper 0 or 1 and apply the checker twice. The search label never changes; the helper returns to its starting value. This demo contains no Z phase mark and does not alter the walkthrough.
* **Test this candidate classically** confirms the selected label’s rule calculation. It is separate from the coherent quantum checker.
* All key selectors inspect the same selected search label. The **Explore output row** selector independently chooses a row in the full joint matrix.
* Step buttons let the presenter choose any snapshot, including Boost to reveal the result directly. They do not apply repeated Grover iterations. **Back** revisits a previous snapshot.
* **Return to prediction (Clear h)** hides the revealed output again and returns to the pre-Boost activity. **Return to Check to predict** revisits the phase question.
* Earn up to five points: one for the phase question and one for each correct key reflection. Points are awarded once per question, and retries are allowed.
* **Restart round** resets the walkthrough, predictions, points, helper demo, and all experiment counts. Changing the lock rule also resets the round. **Clear trials** clears only the selected measurement experiment.

Use Tab to move among controls and arrow keys to adjust the slider. The page supports small screens and reduced-motion preferences.



All calculations run locally in the browser. No data is sent elsewhere.

