# Add Automated CI/CD Testing with Latest C++23 Compilers

## Summary

This PR adds comprehensive GitHub Actions CI/CD workflow for automated testing across multiple platforms and compilers, ensuring code quality on every commit.

## Key Changes

### 🎯 New CI/CD Workflow (`.github/workflows/tests.yml`)

**Linux Testing:**
- ✅ GCC 14 (full C++23 support)
- ✅ Clang 19 (complete C++23 implementation)

**Windows Testing:**
- ✅ MSVC (latest)

**Features:**
- Runs on all pushes and pull requests
- Automated compiler installation
- CMake build configuration
- Test execution with `ctest --output-on-failure`
- Secure: Limited GITHUB_TOKEN permissions (`contents: read`)

### 📝 Documentation Updates

- Updated `README.md` compiler requirements: GCC 14+ and Clang 19+ (previously GCC 13+ and Clang 18+)

## Why This Matters

### Compiler Upgrades

**Problem:** Clang 18 has incomplete C++23 support  
**Solution:** Upgraded to GCC 14 and Clang 19 for mature C++23 implementations

**Benefits:**
- Full C++23 feature availability
- Better standard library support
- Consistent behavior across compilers
- Future-proof for new C++23 features

### Automation Benefits

- **For Contributors:** Immediate test feedback before merging
- **For Maintainers:** Catch issues early, reduce breakage
- **For Users:** Higher quality, more reliable releases

## Testing

✅ All tests passing (8/8 - 100%)
✅ Code review: No issues
✅ Security scan: Zero alerts  
✅ Verified with GCC 14.2.0 locally

## Workflow Structure

```yaml
Jobs:
├── test-linux (ubuntu-24.04)
│   ├── Matrix: [gcc-14, clang-19]
│   └── Steps: checkout → install compiler → cmake → build → test
└── test-windows (windows-latest)
    ├── Compiler: MSVC
    └── Steps: checkout → cmake → build → test
```

## Impact

This establishes automated quality gates for all future development:
- ✨ Every PR gets tested automatically
- 🛡️ Multi-compiler validation prevents compiler-specific bugs
- 🔄 Cross-platform testing ensures Linux/Windows compatibility
- 📊 Clear test results on every commit

---

**Full details**: See [PR_DESCRIPTION.md](./PR_DESCRIPTION.md) for comprehensive documentation.
