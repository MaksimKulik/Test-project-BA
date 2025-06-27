# 📘 API Reference – HubSpot CRM: Contacts Integration

## 🔐 Authentication
<div class="api-box">
  <p><strong>Authorization header:</strong></p>
  <pre><code>Authorization: Bearer YOUR_PRIVATE_APP_TOKEN</code></pre>
</div>

## 📥 Check for Existing Contact
<div class="api-box">
  <p><strong>Method:</strong> <code>GET</code></p>
  <p><strong>Endpoint:</strong> <code>/crm/v3/objects/contacts?email={email}</code></p>

  <p><strong>Headers:</strong></p>
  <pre><code>Content-Type: application/json
Authorization: Bearer YOUR_PRIVATE_APP_TOKEN</code></pre>

  <p><strong>Description:</strong><br>
  Перевіряє, чи існує контакт із зазначеним email у CRM.</p>

<p><strong>Parameters:</strong></p>
  <ul>
    <li><code>email</code>: email клієнта (наприклад, <code>john.doe@example.com</code>)</li>
  </ul>

  <p><strong>Response Codes:</strong></p>
  <ul>
    <li><code>200 OK</code> — список знайдених контактів.</li>
    <li><code>[]</code> — якщо не знайдено.</li>
  </ul>

  <p><strong>Example Response (no match):</strong></p>
  <pre><code>{
  "results": []
}</code></pre>

  <p><strong>Example Response (contact found):</strong></p>
  <pre><code>{
  "results": [
    {
      "id": "123456789",
      "properties": {
        "email": "john.doe@example.com",
        "firstname": "John"
      }
    }
  ]
}</code></pre>
</div>

## 📝 Create New Contact
<div class="api-box">
  <p><strong>Method:</strong> <code>POST</code></p>
  <p><strong>Endpoint:</strong> <code>/crm/v3/objects/contacts</code></p>

  <p><strong>Headers:</strong></p>
  <pre><code>Content-Type: application/json
Authorization: Bearer YOUR_PRIVATE_APP_TOKEN</code></pre>

  <p><strong>Description:</strong><br>
  Створює новий контакт із зазначеним email у CRM.</p>

  <p><strong>Request Body:</strong></p>
  <pre><code>{
  "properties": {
    "firstname": "John",
    "lastname": "Doe",
    "email": "john.doe@example.com",
    "phone": "+380991112233",
    "source": "web_form"
  }
}</code></pre>

  <p><strong>Response Codes:</strong></p>
  <ul>
    <li><code>201 Created</code> — контакт створено успішно.</li>
    <li><code>409 Conflict</code> — конфлікт (наприклад, вже існує).</li>
    <li><code>401 Unathorized</code> — помилка авторизації.</li>
  </ul>

  <p><strong>Success Response:</strong></p>
  <pre><code>{
  "id": "987654321",
  "message": "Contact created successfully.",
  "properties": {
    "email": "john.doe@example.com",
    "firstname": "John"
  }
}</code></pre>

  <p><strong>Error Response (Duplicate):</strong></p>
  <pre><code>{
  "status": "error",
  "message": "Contact already exists"
}</code></pre>
</div>
