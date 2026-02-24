# Cypress

This is unit testing framework used for end-to-end & Component Testing.

---

## Types of Cypress

- **E2E Testing** - End to End Testing
- **Component Testing** - Testing of individual components
- **API Testing** - Testing of API endpoints

---

## Cypress Commands

Cypress uses cy commands like:

- `cy.visit()` - Visit a URL
- `cy.get()` - Get DOM elements
- `cy.click()` - Click on elements
- `cy.type()` - Type into input fields
- `cy.request()` - Make HTTP requests

---

## Example Test Case

**Scenario:** Write a cypress test case for a form with below elements:

1. **Name** - Mandatory field, no special characters, 255 character limit
2. **Submit** - Enable when name is present, disable when no name

**Test Code:**

```javascript
describe('Name Form Validation', () => {

  beforeEach(() => {
    cy.visit('/form') // change to your route
  })

  it('Submit button should be disabled initially', () => {
    cy.get('button[type="submit"]').should('be.disabled')
  })

  it('Submit button should enable when valid name is entered', () => {
    cy.get('input[name="name"]').type('John Doe')
    cy.get('button[type="submit"]').should('not.be.disabled')
  })

  it('Submit button should disable when name field is cleared', () => {
    cy.get('input[name="name"]').type('John')
    cy.get('button[type="submit"]').should('not.be.disabled')

    cy.get('input[name="name"]').clear()
    cy.get('button[type="submit"]').should('be.disabled')
  })

  it('Should show validation error when name is empty (mandatory field)', () => {
    cy.get('input[name="name"]').focus().blur()
    cy.get('.error-message')
      .should('be.visible')
      .and('contain', 'Name is required')
  })

  it('Should not allow special characters', () => {
    cy.get('input[name="name"]').type('John@123!')
    
    cy.get('.error-message')
      .should('be.visible')
      .and('contain', 'Special characters are not allowed')

    cy.get('button[type="submit"]').should('be.disabled')
  })

  it('Should not allow more than 255 characters', () => {
    const longName = 'a'.repeat(256)

    cy.get('input[name="name"]').type(longName)

    cy.get('.error-message')
      .should('be.visible')
      .and('contain', 'Maximum 255 characters allowed')

    cy.get('button[type="submit"]').should('be.disabled')
  })

  it('Should allow exactly 255 characters', () => {
    const validName = 'a'.repeat(255)

    cy.get('input[name="name"]').type(validName)
    cy.get('button[type="submit"]').should('not.be.disabled')
  })

})
```

---