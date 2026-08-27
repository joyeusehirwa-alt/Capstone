# PROPOSAL.md

## 1. Problem Statement and Target User

Homeowners in planned urban redevelopment zones often live with unresolved property damage  leaking roofs, mold  because getting a basic repair permit requires tracking down a local leader (such as a sector executive secretary) who has little incentive to respond quickly. Renovating a home raises its assessed value, and a higher value means the local authority owes more when the property is eventually taken for redevelopment. As a result, requests are frequently delayed, verbally postponed, or simply ignored, with no official record showing that this happened.

Target users are urban property owners seeking repair/renovation permits in these zones, and secondarily, municipal oversight committees who would benefit from visibility into how these requests are being handled.

## 2. Proposed Approach

The project is a web-based submission portal where a resident:
1. Submits a photo of the property damage along with a short text description.
2. Has the photo evaluated by an image-recognition model (a pre-trained model such as MobileNet, fine-tuned on damage-classification data) that assigns an objective urgency score (e.g., minor, moderate, severe).
3. Receives a timestamped digital record of the request, which functions as a trackable ticket rather than an informal, undocumented ask.
4. Has their request automatically escalated to a higher oversight authority if it goes unanswered past a defined response window.

The text description serves as a backup context layer for cases where the image model may misjudge unfamiliar building materials or local construction styles.

## 3. Data

- **Source**: Open-source structural/building damage datasets (e.g., Kaggle concrete crack or mold classification datasets) for training/fine-tuning the initial model, combined with synthetic local permit metadata (timestamps, urgency tags, status history) to simulate and test the request-tracking workflow.
- **Format**: Images (JPEG/PNG) for damage classification; structured metadata (JSON/CSV) for request records.
- **Open question**: We do not yet have access to real local damage photos or real permit request histories from the target town. It is an open question whether we can obtain even a small local sample for validation, or whether the prototype will need to rely entirely on open datasets and synthetic data for this phase.

## 4. Success Criteria

The project will be considered successful if:
- A resident can submit a photo and description through the portal and receive an urgency rating within seconds.
- Every submitted request generates a timestamped, retrievable record (i.e., nothing submitted through the system can be silently lost or denied without a trace).
- Requests that pass a defined time threshold without a status update are visibly flagged/escalated in the system.
- A non-technical reviewer (e.g., an instructor or classmate unfamiliar with the project) can use the portal and correctly understand their request's status without help.

## 5. Scope Cut

For this phase, the project will **not** include actual integration with local government systems or authority (i.e., it will not be an officially adopted tool by any sector or municipal office). Building real institutional integration would require partnerships and approvals outside this timeline. Instead, the prototype will demonstrate the full workflow (submission → scoring → tracking → escalation) as a standalone system that could later be piloted with a real local office.
