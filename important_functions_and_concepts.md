# أهم الدوال والمفاهيم للـ QA في Unit Testing

```python
# 1. assert
# تتأكد من صحة النتائج المتوقعة
assert add(2, 3) == 5
assert login("user", "pass") == True

# 2. setup و teardown
# تستخدم لتجهيز البيئة قبل الاختبار وتنظيفها بعده
def setup_function():
    print("تجهيز البيانات قبل الاختبار")

def teardown_function():
    print("تنظيف بعد انتهاء الاختبار")

# 3. test_
# كل دالة اختبار يجب أن تبدأ بـ test_ ليتم التعرف عليها
def test_login_success():
    assert login("admin", "1234") == True

# 4. mock / patch
# لمحاكاة الكود الخارجي أو الأنظمة الأخرى
from unittest.mock import patch

with patch('module.api_call') as mock_api:
    mock_api.return_value = {"status": "success"}
    assert api_call() == {"status": "success"}

# 5. Expected Result مقابل Actual Result
expected = 5
actual = add(2, 3)
assert actual == expected

# 6. assertEqual, assertTrue, assertFalse
# تستخدم في مكتبة unittest
import unittest

class TestExample(unittest.TestCase):
    def test_math(self):
        self.assertEqual(add(2, 3), 5)
        self.assertTrue(is_logged_in)
        self.assertFalse(has_error)

# 7. Test Case و Test Suite
# Test Case = اختبار واحد
# Test Suite = مجموعة اختبارات
def test_add():
    assert add(2, 3) == 5

# 8. setUpClass و tearDownClass
# تجهيز البيئة مرة واحدة لكل الاختبارات داخل كلاس
class TestMath(unittest.TestCase):

    @classmethod
    def setUpClass(cls):
        print("تجهيز بيانات قبل كل الاختبارات في الكلاس")

    @classmethod
    def tearDownClass(cls):
        print("تنظيف بعد كل الاختبارات في الكلاس")
