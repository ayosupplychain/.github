# .github
Actions starter templates

## Golden pipeline starters

The `workflow-templates` directory includes optional Python CI and release workflow
starters. Selecting a starter copies a workflow into your repository; it does not
enforce adoption. Organization rulesets and repository settings are managed separately
and remain the enforcement mechanism.

These examples call reusable workflows from
[`ayosupplychain/org-workflows`](https://github.com/ayosupplychain/org-workflows)
at the `v1` release. The golden build currently expects a Python project with
`requirements.txt` and pytest tests. It defaults to Python 3.12. Adapt the build
for other languages rather than treating these Python examples as universal.

The caller workflows grant `id-token: write` and `attestations: write` because
the reusable build creates provenance and SBOM attestations, and the deploy
workflow uses OIDC. To use the release starter, configure the `staging` and
`production` environments, ensure the required runner groups are available,
and provide the change-request input for production deployments. The demo's
change-request check is simulated.

The CI starter also runs the governance scan on pushes to the default branch;
that job needs `actions: read` and `security-events: write` to publish findings.
The scan reports existing issues, while any ruleset-required workflow remains a
separate enforcement control.

These templates are intended for private or internal repositories in
`ayosupplychain`. The caller repository must be allowed to use the reusable
workflows in `org-workflows`; while that repository remains internal, public
repositories cannot call these workflows.
