# Integration review

## Pinned inputs

The root tree pins the three inputs below. These are the only revisions that may
be used for the review; updating a gitlink to a newer revision is out of scope.

| Submodule | Pinned commit |
| --- | --- |
| `adns` | `31fbc0f4ce5f06a1c05ccc936ef080a1313f8421` |
| `agent-hosting` | `0f25b0e6bf4a6345a5d6c1c014bac999cf435d7d` |
| `herdr` | `101ccc20d3c6483a38ed9e0a1239b2ab908b1704` |

## Checkout and verification status

Run the following from the repository root:

```sh
git submodule update --init --recursive
git submodule status
test "$(git -C adns rev-parse HEAD)" = 31fbc0f4ce5f06a1c05ccc936ef080a1313f8421
test "$(git -C agent-hosting rev-parse HEAD)" = 0f25b0e6bf4a6345a5d6c1c014bac999cf435d7d
test "$(git -C herdr rev-parse HEAD)" = 101ccc20d3c6483a38ed9e0a1239b2ab908b1704
```

In the current review environment, registration succeeded but GitHub denied
all three HTTPS clone requests at the network proxy (`CONNECT ... 403`). The
submodule worktrees therefore contain neither source nor documentation, and
their pinned objects are not present in the root object database. Consequently,
source/documentation presence cannot truthfully be confirmed here.

No submodule revision was advanced: the three gitlinks in the root tree remain
at the commits above.

## Review disposition

The requested code review is blocked on obtaining those exact objects. In
particular, it would be unsafe to name reusable components or concrete symbols
from a branch tip, a different revision, or memory and present them as findings
from the pinned source.

Once the pinned worktrees are available, repeat the review against these exact
areas and record file paths and symbols alongside every conclusion:

1. ADNS registration, evidence verification, DNS records, certificates, and
   policy enforcement.
2. Agent Hosting attestation issuance and attestation validation.
3. HERDR listener setup, instance lifecycle, multiplexing, deployment, and
   client connection establishment.

### Reuse and integration findings

No ADNS or Agent Hosting component is currently classified as directly reusable,
and no HERDR integration point is currently claimed. This means **not reviewed**,
not **none exist**. Concrete path-and-symbol findings require the exact pinned
source and documentation to be present first.
