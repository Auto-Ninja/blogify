🔐 What Is Encapsulation?
Encapsulation means:
Wrapping data (fields) and methods (functions) that operate on that data into a single unit—usually a class—and restricting direct access to some of the object's components.


🧩 In Practice (Java Example)
public class Product {
    private int id;           // Private field
    private String name;

    public int getId() {      // Public getter
        return id;
    }

    public void setId(int id) { // Public setter
        this.id = id;
    }
}


- id is private: it can’t be accessed directly from outside the class.
- getId() and setId() are public: they provide controlled access.

🎯 Why Is Encapsulation Useful?
- ✅ Security: Prevents unwanted changes to internal data.
- ✅ Control: You can add validation (e.g., reject negative prices).
- ✅ Flexibility: You can change internal implementation without affecting other code.
- ✅ Maintainability: Easier to debug and update.

🧠 Analogy
Think of a vending machine:
- You press buttons (public methods).
- You don’t see the internal wiring or mechanics (private fields).
- You get your snack without needing to understand how it works.
