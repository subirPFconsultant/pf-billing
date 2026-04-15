
<!DOCTYPE html>
<html>
<head>
  <title>PF Billing System</title>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.9.2/html2pdf.bundle.min.js"></script>

  <style>
    body {
      font-family: Arial;
      background: #f2f2f2;
      padding: 20px;
    }

    /* FORM DESIGN */
    .form-box {
      max-width: 400px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px gray;
    }

    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
    }

    button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      background: green;
      color: white;
      border: none;
      cursor: pointer;
      font-size: 16px;
    }

    /* INVOICE (PDF) DESIGN */
    #invoice {
      visibility: hidden;
      position: absolute;
      left: -9999px;
      width: 800px;
      background: white;
      padding: 20px;
    }

    .header {
      display: flex;
      justify-content: space-between;
      border-bottom: 2px solid black;
      padding-bottom: 10px;
    }

    .logo {
      width: 100px;
    }

    h2, h3 {
      margin: 0;
    }

    table {
      width: 100%;
      margin-top: 20px;
      border-collapse: collapse;
    }

    table, th, td {
      border: 1px solid black;
      padding: 10px;
      text-align: left;
    }

    .total {
      text-align: right;
      margin-top: 10px;
      font-size: 18px;
      font-weight: bold;
    }

    .qr {
      text-align: center;
      margin-top: 30px;
    }

    .qr img {
      width: 120px;
      border: 1px solid black;
      padding: 5px;
    }

    .footer {
      text-align: center;
      margin-top: 20px;
      font-weight: bold;
    }

  </style>
</head>

<body>

<!-- SIMPLE FORM -->
<div class="form-box">
  <h2>Billing Entry</h2>

  <input id="name" placeholder="Customer Name">
  <input id="mobile" placeholder="Mobile Number">
  <input id="uan" placeholder="UAN Number">
  <input id="service" placeholder="Service Details">
  <input id="amount" type="number" placeholder="Amount (₹)">

  <select id="status">
    <option>Paid</option>
    <option>Unpaid</option>
  </select>

  <button onclick="generatePDF()">Download Invoice</button>
</div>

<!-- PROFESSIONAL INVOICE -->
<div id="invoice">

  <div class="header">
    <div>
      <h2>PF Consultant Service</h2>
      <p>West Bengal, South 24 Parganas, Namkhana, Patibunia - 743357</p>
      <p>Mobile: 7365996618 | WhatsApp: 9775515990</p>
      <p>Email: subir.das7365@gmail.com</p>
    </div>

    <img src="https://instasize.com/p/16b63c2748e208b0b90557a642dd499cdd1143cb59d54632908c8efdc80d1654" class="logo">
  </div>

  <h3 style="margin-top:10px;">INVOICE</h3>

  <p><b>Invoice No:</b> <span id="inv"></span></p>
  <p><b>Date:</b> <span id="date"></span></p>

  <table>
    <tr>
      <th>Name</th>
      <th>Mobile</th>
      <th>UAN</th>
      <th>Service</th>
      <th>Status</th>
    </tr>

    <tr>
      <td id="cname"></td>
      <td id="cmobile"></td>
      <td id="cuan"></td>
      <td id="cservice"></td>
      <td id="cstatus"></td>
    </tr>
  </table>

  <div class="total">
    Total Amount: ₹<span id="camount"></span>
  </div>

  <div class="qr">
    <h3>Payment</h3>
    <img src="https://instasize.com/p/e90e86d1ff81e24da711315ea0599e19ddbd349457d723b060ba9d4b98ed7ef7">
    <p>QR কোড স্ক্যান করে আপনার বাকি টাকা পরিশোধ করুন।</p>
    <p>Payment করার পর আমাদের জানাবেন।</p>
  </div>

  <div class="footer">
    Thank You for Choosing Our Service
  </div>

</div>

<script>
function generatePDF() {

  document.getElementById("inv").innerText = Math.floor(Math.random()*100000);
  document.getElementById("date").innerText = new Date().toLocaleDateString();

  document.getElementById("cname").innerText = document.getElementById("name").value;
  document.getElementById("cmobile").innerText = document.getElementById("mobile").value;
  document.getElementById("cuan").innerText = document.getElementById("uan").value;
  document.getElementById("cservice").innerText = document.getElementById("service").value;
  document.getElementById("cstatus").innerText = document.getElementById("status").value;
  document.getElementById("camount").innerText = document.getElementById("amount").value;

  let invoice = document.getElementById("invoice");

  invoice.style.visibility = "visible";
  invoice.style.position = "static";

  setTimeout(() => {
    html2pdf().from(invoice).save("PF_Invoice.pdf");

    invoice.style.visibility = "hidden";
    invoice.style.position = "absolute";
    invoice.style.left = "-9999px";
  }, 500);
}
</script>

</body>
</html>
</html>
