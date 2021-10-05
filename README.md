# Cynomi GirHub Actions


## Use the extract-branch action to get a branch and slug (replace `/` with `-`)

```
name: Test extract-branch
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - id: extract-branch
        uses: Cynomi/actions/extract-branch@main
        with:
          ref: ${{ github.ref }}
      - name: Access branch
        run: echo Branch is ${{ steps.extract-branch.outputs.branch }}
      - name: Access branch
        run: echo Slug is ${{ steps.extract-branch.outputs.slug }}
```

## Use the pulumi action

```
name: Test pulumi
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-region: ${{ secrets.AWS_REGION }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
      - name: Run pulumi up
        uses: Cynomi/actions/pulumi@main
        with:
          command: up
          stack-name: the-name-of-the-stack
```
