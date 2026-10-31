# Historical handoff rollover dry-run verification

- Source commit: `b80c4265c765c77b5eeba8ab91a354abccd6c568`
- Source blob: `a8b9154613cecb308c27b55535c19ac11bdc9b5a`
- Source SHA-256: `CB8D16FADE121A5E9A134AF13061B0463102ACBE555F70B6FF36E5854BEEA6ED`
- Source bytes: 950661
- Preamble bytes: 30
- Complete entries: 154
- Overall verification: PASS

| File | Ordinals | Entries | Header bytes | Entry bytes | Total bytes | State | SHA-256 |
|---|---:|---:|---:|---:|---:|---|---|
| Handoff-history-001.md | 111-154 | 44 | 415 | 432128 | 432543 | Closed | `2C48E5582AC53805D474B3B051C70B1EAA5546AB37D1480A3DB2AFA7A5A0431F` |
| Handoff-history-002.md | 11-110 | 100 | 415 | 499424 | 499839 | Closed | `0804D0F51FEEC2A42CBC0B779E4200E7EFFE4679065AF0B52806CC97107F9186` |
| Handoff-history-003.md | 1-10 | 10 | 410 | 19079 | 19489 | Open | `CDF9D5E7C61127C00B2C148C47185CBAEC6A3778077C47587F5522D99357FDF4` |

## Checks

- complete_entry_count_154: True
- ordinals_exactly_once_in_source_order: True
- per_entry_hashes_unchanged: True
- reconstruction_byte_equal: True
- reconstruction_length_equal: True
- reconstruction_sha256_equal: True
- ordinary_volumes_within_500000: True
- index_links_resolve: True
- plain_history_references_resolve: True
- git_reference_token_multiset_unchanged: True

Generated artifacts are temporary proposals only; no tracked file or remote ref was modified.
