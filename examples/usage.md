# Usage Notes: Constructing a Confidential Spend using the Vault contract

This example describes, at a high level, how you'd use the vault contract when creating a spend in Elements/Liquid:

1. **Create the funding output (confidential UTXO)**
   - Issue a PSET (Partially Signed Elements Transaction) or raw transaction that creates an output whose locking script is the Simplicity commitment (the `spend_vault` script).
   - The output must be constructed as a Confidential Transaction: amounts and asset types are blinded; the scriptPubKey commits to the Simplicity program.

2. **Peg-in / Peg-out**
   - Use Liquid peg-in to get L-BTC if needed.
   - The Simplicity contract operates on Elements/Liquid UTXOs.

3. **Spending**
   - To spend, the spender prepares a PSET that consumes the vault UTXO.
   - Include witness fields required by the Simplicity program:
     - Serialized arguments (sigmask, signatures, pubkeys, locktimes, etc.)
     - Current blockheight (or pass via input's sequence/locktime depending on convention)
   - Signers produce signature blobs compatible with ECVerify combinators expected by the compiled Simplicity program.

4. **Blinding**
   - Preserve confidentiality by performing blinding operations on the transaction using Elements blinding tools prior to broadcasting.
   - Range proofs and surjection proofs are handled by the Elements wallet library and are orthogonal to the Simplicity contract.

5. **Validation**
   - When the node or Elements interpreter evaluates the Simplicity program, it will verify signatures and time conditions and return allowed/disallowed.

Notes:
- Real implementations must map Simplicity input encoding exactly to how PSET and witness data are presented to the on-chain interpreter.
- Multi-party signing flows must coordinate to assemble signature blobs and PSET fields.


