# 🚀 Jenkins Pipeline as Code - Post Actions

## 🎯 Objective

Demonstrate Jenkins Pipeline Post Actions:

* ✅ Always
* ✅ Success
* ✅ Failure

---

## 📋 Prerequisites

* Jenkins Server Running
* Existing Pipeline Job: `Pipeline-as-code-Hello-world`

---

# 🧪 Demo 1 - Always Post Action

## 📝 Steps

1. Open Jenkins Dashboard.
2. Open `Pipeline-as-code-Hello-world`.
3. Click **Configure**.
4. Add the following code:

```groovy
post {
    always {
        echo 'I will always say Hello again!'
    }
}
```

5. Save the pipeline.
6. Click **Build with Parameters**.
7. Verify that the build is successful.
8. Verify the following output:

```text
I will always say Hello again!
```

---

# 🧪 Demo 2 - Failure Post Action

## 📝 Steps

1. Open `Pipeline-as-code-Hello-world`.
2. Click **Configure**.
3. Introduce an intentional error:

```groovy
stage('Deploy on prod') {
    steps {
        echo12 'Deploy on prod1'
    }
}
```

4. Add the following Post Actions:

```groovy
post {
    always {
        echo 'I will always say Hello again!'
    }

    failure {
        echo 'failure !'
    }

    success {
        echo 'success !'
    }
}
```

5. Save the pipeline.
6. Click **Build with Parameters**.
7. Wait for the build to fail.
8. Open the build output.
9. Verify the following output:

```text
I will always say Hello again!
failure !
```

---

# 🧪 Demo 3 - Success Post Action

## 📝 Steps

1. Open `Pipeline-as-code-Hello-world`.
2. Click **Configure**.
3. Fix the error:

```groovy
stage('Deploy on prod') {
    steps {
        echo 'Deploy on prod1'
    }
}
```

4. Save the pipeline.
5. Click **Build with Parameters**.
6. Wait for the build to complete successfully.
7. Open the build output.
8. Verify the following output:

```text
I will always say Hello again!
success !
```

---

# ✅ Verification

### ❌ Failed Build

```text
I will always say Hello again!
failure !
```

### ✅ Successful Build

```text
I will always say Hello again!
success !
```

---

# 🎉 Conclusion

| Post Action | Description                       |
| ----------- | --------------------------------- |
| `always`    | Runs after every build            |
| `success`   | Runs only when the build succeeds |
| `failure`   | Runs only when the build fails    |

This demo shows how Jenkins Post Actions can be used to execute tasks after pipeline execution based on build status.
